```
Rational{T}(obj::GapObj) where {T<:Integer}
```

[GAP整数](GAP_ref(ref:Integers))または[GAP有理数](GAP_ref(ref:Rationals)) `obj`から変換された有理数を返します。

# 例

```jldoctest
julia> val = GAP.Globals.Factorial(25)
GAP: 15511210043330985984000000

julia> Rational{Int128}(val)
15511210043330985984000000//1

julia> Rational{BigInt}(val)
15511210043330985984000000//1

julia> val = GAP.Obj(1//3)
GAP: 1/3

julia> Rational{Int64}(val)
1//3

```
