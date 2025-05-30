```
KnotPointObjective(
    ℓ::Function,
    names::AbstractVector{Symbol},
    traj::NamedTrajectory,
    params::AbstractVector;
    kwargs...
)
KnotPointObjective(
    ℓ::Function,
    names::AbstractVector{Symbol},
    traj::NamedTrajectory;
    kwargs...
)
KnotPointObjective(
    ℓ::Function,
    name::Symbol,
    args...;
    kwargs...
)
```

軌道最適化のためのノットポイント合計目的関数を作成します。ここで、`ℓ(x, p)` は軌道ノットポイント変数 `x` とパラメータ `p` に依存します。パラメータ引数が省略された場合、`ℓ(x)` は `x` のみの関数であると見なされます。

# 引数

  * `ℓ::Function`: 目的を定義する関数、ℓ(x, p) または ℓ(x)。
  * `names::AbstractVector{Symbol}`: 最適化される軌道変数の名前。
  * `traj::NamedTrajectory`: 目的が定義される軌道。
  * `params::AbstractVector`: 各時刻の目的関数 ℓ のためのパラメータ `p`。

# キーワード引数

  * `times::AbstractVector{Int}=1:traj.T`: 目的が評価される時刻インデックス。
  * `Qs::AbstractVector{Float64}=ones(traj.T)`: 各時刻における目的関数の重み。
