```
BackwardSearchGoal(goal::Goal, start::State)
```

逆方向探索のために使用される目標仕様（例：[`BackwardPlanner`](@ref））で、元の`goal`仕様と、目標から逆方向探索を通じて到達すべき`start`状態から構成されます。
