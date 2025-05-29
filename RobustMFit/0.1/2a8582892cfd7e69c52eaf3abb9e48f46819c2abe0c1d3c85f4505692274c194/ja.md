```
w(z::Real, spec::MSetting)
```

M推定の重み関数であり、`spec`は使用する関数の仕様です。ψ(z, spec)/zを計算します。

# 例

```julia
w(1.5, Huber(1.5, ϵ = 0.1))
w(1, Tukey(4.5, 6))
w(1.5, Andrew(4.5, 6))
w(1.5, Hampel([1, 3, 7])
```

他にも[`ρ`](@ref ρ)、[`ψ`](@ref ψ)および[`ψder`](@ref ψder)を参照してください。
