```
showbasis(α::Vector{<:Real},β::Vector{<:Real};sym::String,digits::Integer)
```

再帰係数 `α`, `β` に基づいてすべての基底多項式を表示します。キーワード `sym` は変数の名前を設定し、`digits` は表示される桁数を制御します。

```jldoctest
julia> using PolyChaos

julia> α, β = rm_hermite(5);

julia> showbasis(α, β)
1
x
x^2 - 0.5
x^3 - 1.5x
x^4 - 3.0x^2 + 0.75
x^5 - 5.0x^3 + 3.75x
```

`PolyChaos.jl` の型に合わせて調整されています。

```
showbasis(op::AbstractOrthoPoly;sym::String,digits::Integer)
```

`AbstractOrthoPoly` のすべての基底多項式を表示します。

```jldoctest
julia> using PolyChaos

julia> op = LegendreOrthoPoly(4);

julia> showbasis(op)
1
x
x^2 - 0.33
x^3 - 0.6x
x^4 - 0.86x^2 + 0.09
```
