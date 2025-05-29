```
is_nilpotent(a::T) where {T <: NCRingElement}
```

返すのは真である場合のみ $a$ がニルポテントである、すなわちある $k$ に対して $a^k == 0$ である。

# 例

```jldoctest
julia> R, _ = residue_ring(ZZ,720);

julia> S, x = polynomial_ring(R, :x);

julia> is_nilpotent(30*x), is_nilpotent(30+90*x), is_nilpotent(S(15))
(true, true, false)
```
