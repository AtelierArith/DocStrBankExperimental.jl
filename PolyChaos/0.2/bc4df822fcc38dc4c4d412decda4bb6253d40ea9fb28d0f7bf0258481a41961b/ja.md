```
showpoly(coeffs::Vector{<:Real};sym::String,digits::Integer)
```

係数 `coeffs` を持つ単項式多項式を人間が読みやすい形で表示します。キーワード `sym` は変数の名前を設定し、`digits` は表示する桁数を制御します。

```jldoctest
julia> using PolyChaos

julia> showpoly([1.2, 2.3, 3.4456])
x^3 + 3.45x^2 + 2.3x + 1.2

julia> showpoly([1.2, 2.3, 3.4456], sym = "t", digits = 2)
t^3 + 3.45t^2 + 2.3t + 1.2
```

```
showpoly(d::Integer,α::Vector{<:Real},β::Vector{<:Real}; sym::String,digits::Integer)
showpoly(d::Range,α::Vector{<:Real},β::Vector{<:Real};sym::String,digits::Integer) where Range <: OrdinalRange
```

再帰係数 `α`、`β` を持つ次数/範囲 `d` の単項式多項式を表示します。

```jldoctest
julia> using PolyChaos

julia> α, β = rm_hermite(10)
([0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0], [1.77245, 0.5, 1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5])

julia> showpoly(3, α, β)
x^3 - 1.5x

julia> showpoly(0:2:10, α, β)
1
x^2 - 0.5
x^4 - 3.0x^2 + 0.75
x^6 - 7.5x^4 + 11.25x^2 - 1.88
x^8 - 14.0x^6 + 52.5x^4 - 52.5x^2 + 6.56
x^10 - 22.5x^8 + 157.5x^6 - 393.75x^4 + 295.31x^2 - 29.53
```

`PolyChaos.jl` の型に合わせて調整されています。

```
showpoly(d::Union{Integer,Range},op::AbstractOrthoPoly;sym::String,digits::Integer) where Range <: OrdinalRange
```

`AbstractOrthoPoly` の次数/範囲 `d` の単項式多項式を表示します。

```jldoctest
julia> using PolyChaos

julia> op = GaussOrthoPoly(5);

julia> showpoly(3, op)
x^3 - 3.0x

julia> showpoly(0:(op.deg), op; sym = "t")
1
t
t^2 - 1.0
t^3 - 3.0t
t^4 - 6.0t^2 + 3.0
t^5 - 10.0t^3 + 15.0t
```

[この機能を提供してくれた @pfitzseb に感謝します。](https://discourse.julialang.org/t/how-to-define-verbose-output-for-a-polynomial/21317/5)
