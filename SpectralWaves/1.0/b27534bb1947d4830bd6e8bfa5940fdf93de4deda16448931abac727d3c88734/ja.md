```
fourier_transform(f::Vector{<:Number}, ω::Real, x::AbstractRange{<:Real})
```

関数値 `f` を点 `x` で使用して `f̂(ω)` を計算します。

# 例

```julia-repl
julia> f = [-1, 0, 1, 0, -1]; ω = 1; x = range(-π, π, length = 5);
julia> fourier_transform(f, ω, x)
0.5 + 0.0im
```
