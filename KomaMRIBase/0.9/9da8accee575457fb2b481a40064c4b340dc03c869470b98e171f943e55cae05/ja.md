```
motion = Motion(action)
motion = Motion(action, time)
motion = Motion(action, time, spins)
```

Motion構造体。これは、特定の時間間隔における、与えられたスピンのグループの動きを定義します。これは、3つのフィールドで構成されています：`action`は動きを定義し、`time`は動きが行われる時間を考慮し、`spins`はその動きに影響を受けるスピンを示します。

# 引数

  * `action`: (`::AbstractAction{T<:Real}`) [`Translate`](@ref)や[`Rotate`](@ref)などのアクション
  * `time`: (`::TimeCurve{T<:Real}`, `=TimeRange(0.0)`) 動きに関する時間情報
  * `spins`: (`::AbstractSpinSpan`, `=AllSpins()`) 動きに影響を受けるスピンのインデックス

# 戻り値

  * `motion`: (`::Motion`) Motion構造体

# 例

```julia-repl
julia> motion =  Motion(
            action = Translate(0.01, 0.0, 0.02),
            time = TimeRange(0.0, 1.0),
            spins = SpinRange(1:10)
       )
```
