```
inverse_fourier_transform(f̂::Vector{<:Number}, ω::AbstractRange{<:Real}, x::Real)
```

展開振幅 `f̂` と固有値 `ω` を使用して `f(x)` を計算します。

# 例

```julia-repl
julia> f̂ = [0.5, 0, 0.5]; ω = -1:1; x = π; inverse_fourier_transform(f̂, ω, x)
-1.0
```
