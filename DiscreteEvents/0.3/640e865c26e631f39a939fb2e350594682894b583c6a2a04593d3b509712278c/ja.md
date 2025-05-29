```
tau(clk::Clock=𝐶)
```

現在のシミュレーション時間を返します。

# 例

```jldoctest
julia> using DiscreteEvents

julia> resetClock!(𝐶)   # デフォルトの時計をリセット
"clock reset to t₀=0.0, sampling rate Δt=0.01."
julia> tau()            # デフォルトの時計の時間を取得
0.0
```
