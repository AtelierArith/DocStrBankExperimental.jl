```
CircularMaze(n_corridors::Integer, corridor_length::Integer, discount::Float64, r_findgoal::Float64, r_timestep_penalty::Float64)
CircularMaze(n_corridors::Integer, corridor_length::Integer; kwargs...)
CircularMaze()
```

円形迷路環境を表すPOMDPです。

# フィールド

  * `n_corridors::Integer`: 円形迷路内の廊下の数。
  * `corridor_length::Integer`: 各廊下の長さ。
  * `probabilities::AbstractArray`: ボン・ミーゼス分布を作成するための確率質量。
  * `center::Integer`: 迷路内の中心位置。
  * `discount::Float64`: 将来の報酬に対する割引率。
  * `r_findgoal::Float64`: 目標を見つけたときの報酬。
  * `r_timestep_penalty::Float64`: 取られた各タイムステップに対するペナルティ。
  * `states::AbstractArray`: 迷路内のすべての可能な状態の配列。
  * `goals::AbstractArray`: 迷路内の目標状態の配列。

# 例

```julia
using CompressedBeliefMDPs

n_corridors = 8
corridor_length = 25
maze = CircularMaze(n_corridors, corridor_length)
```
