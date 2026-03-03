# 🐱 Kitty's Food Quest – A Q‑learning Maze Game

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/KittyFoodQuest/blob/main/KittyFoodQuest.ipynb)

This project demonstrates a **tabular Q‑learning** agent learning to navigate a 6×6 grid world. The goal is to reach the food while avoiding fixed water pits. The agent receives dense rewards through step penalties, wall penalties, and **reward shaping** based on Manhattan distance to the food.

## 🎮 Game Rules

- **Grid size**: 6×6  
- **Cat start**: `[0,0]` (top‑left)  
- **Food location**: `[5,5]` (bottom‑right)  
- **Water pits** (fixed): `[1,3]`, `[2,2]`, `[3,4]`, `[4,1]`  
- **Actions**: Up, Down, Left, Right (4 discrete actions)  
- **Rewards**:
  - Step cost: `-0.1`
  - Wall penalty: `-1.0` (if move would go out of bounds)
  - Reward shaping: `(old_dist – new_dist) * 0.5` (encourages moving toward food)
  - Food reached: `+10`
  - Water pit: `–10`

## 🧠 Q‑learning Algorithm

- **State representation**: string `"[x,y]"` (e.g., `"[0,0]"`) for compatibility with pandas.
- **Q‑table**: pandas DataFrame storing action values.
- **Exploration**: ε‑greedy policy with ε starting at `1.0` and decaying by `0.995` each episode to a minimum of `0.05`.
- **Learning rate** `α = 0.1`, discount factor `γ = 0.9`.
- **Optimistic initialisation**: new states get Q‑values of `5.0` to encourage exploration.
- **Training**: up to 200 episodes, max 50 steps per episode. Early stopping after 10 consecutive victories.

## 📁 Repository Structure
