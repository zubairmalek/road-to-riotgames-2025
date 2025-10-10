# Design Document — Corner Clash (Valorant-Inspired Prototype)

## 1. Problem & Goal
Create a small, turn-based prototype that demonstrates my understanding of software-engineering principles such as object-oriented programming, data structures, and algorithmic thinking.

The concept: two agents (a player and an opponent) battle across **four corners** of a grid. Each round, both choose where to move and where to attack. If an attack targets the corner containing the opponent, it hits. If both move into the same corner, they collide and take minor damage before resetting.

This project is part of my **Road-to-RiotGames 2025** learning sprint, showing how I apply MSc Computer Science concepts in practice.

---

## 2. Core Gameplay Loop
- The board has four corners:
  - Top-Left (TL)
  - Top-Right (TR)
  - Bottom-Left (BL)
  - Bottom-Right (BR)
- Each round:
  1. Player chooses one corner to **move** to.
  2. Player chooses one corner to **attack**.
  3. The AI opponent randomly chooses a move and attack corner.
  4. **Resolution phase:**
     - If a player attacks the corner where the opponent currently is → **hit (full damage)**.
     - If both players move into the same corner → **collision (minor damage to both)** and they reset to previous positions.
     - Otherwise → **miss** (no damage).
  5. Check HP → game ends when a player's HP ≤ 0.
  6. Display round results (hit/miss/collision) and HP after each round.

---

## 3. Technical Stack
- **Language:** Python 3.11  
- **Libraries:**  
  - `pygame` (for visuals, optional)
  - `pytest` (for testing later)
- **Tools:** VS Code, Git, GitHub  
- **Branching:** `main` (stable) and `dev` (active development)

---

## 4. Data Structures
- **Corners:**  
  Represented as a dictionary mapping corner names to coordinates, e.g.  
  `{ "TL": (0,0), "TR": (1,0), "BL": (0,1), "BR": (1,1) }`.
- **Agent State:**  
  Each agent will be represented by a class instance holding attributes like `name`, `hp`, `corner`, and `prev_corner`.
- **Turn Tracking:**  
  Simple counter or a queue structure to manage alternating turns.
- **Attack Result:**  
  Represented by strings or an enum such as `"hit"`, `"miss"`, or `"collision"`.

---

## 5. Core Classes (initial design)
- **Agent**
  - Attributes: `name`, `hp`, `corner`, `prev_corner`
  - Methods: `move_to(corner)`, `reset_position()`
- **Game**
  - Attributes: `agents`, `corners`, `round`
  - Methods: `resolve_turns(player_move, player_attack, ai_move, ai_attack)`, `check_collision()`, `check_hit()`, `apply_damage()`
- **AI**
  - Randomly chooses move and attack corners.

---

## 6. Risks & Scope Limits
- Time constraint (3 weekends total).
- Visuals will be minimal — simple text-based or rectangle displays.
- AI logic starts random; pathfinding or prediction can come later.
- Pygame optional — main focus is on working terminal logic.
- Prioritize clear code, documentation, and structure over graphics.

---

## 7. Milestones
- **Milestone 1:** Terminal prototype (player and AI rounds working).  
- **Milestone 2:** Add OOP refactor, collision and damage logic.  
- **Milestone 3:** Optional Pygame interface for visual version.  
- **Milestone 4:** Polish README, add Dev Journal reflections, and record a demo GIF.  

---

## 8. Learning Outcomes
- Apply MSc concepts in a practical coding context:
  - OOP design and abstraction
  - Data structures (dicts, queues)
  - Algorithmic thinking and conditional logic
  - Software engineering workflow (Git branching, documentation)
- Practice writing clear, maintainable code and documenting reasoning.

---

## 9. Future Extensions
- Additional abilities (e.g. Dash, Heal, Area Attack).
- Smarter AI (probability-based prediction).
- User interface for move and attack selection.
- Add sound or basic animation with Pygame.

---
