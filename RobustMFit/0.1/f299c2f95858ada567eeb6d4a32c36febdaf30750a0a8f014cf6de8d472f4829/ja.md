```
ρ(z::Real, spec::MSetting)
```

M推定の損失関数であり、`spec`は使用する関数の仕様です。

# 例

```julia
ρ(1.5, Huber(1.5, ϵ = 0.1))
ρ(1, Tukey(4.5, 6))
ρ(1.5, Andrew(4.5, 6))
ρ(1.5, Hampel([1, 3, 7])
```

他にも[`ψ`](@ref ψ)、[`ψder`](@ref ψder)および[`w`](@ref w)を参照してください。
