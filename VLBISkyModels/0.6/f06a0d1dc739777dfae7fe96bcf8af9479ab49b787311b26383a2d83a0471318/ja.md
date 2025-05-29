```julia
struct Shift{T, T1, T2} <: VLBISkyModels.ModelModifier{T}
```

モデルをx方向に`Δx`ユニット、y方向に`Δy`ユニットシフトします。

# 例

```julia-repl
julia> modify(Gaussian(), Shift(2.0, 1.0)) == shifted(Gaussian(), 2.0, 1.0)
true
```
