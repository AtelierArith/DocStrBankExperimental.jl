```
is_zero(R::NCRing)
```

環 $R$ が自明であるかどうかをテストします。ただし、これを行うための推奨される方法は [`is_trivial`](@ref) です。

```jldoctest
julia> R, (x,) = polynomial_ring(QQ, [:x]);

julia> S=quo(R,1)[1]
1による剰余環 R

julia> is_trivial(S)
true

julia> is_zero(S)
true
```
