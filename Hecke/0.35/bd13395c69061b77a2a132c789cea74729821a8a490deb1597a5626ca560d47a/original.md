```
absolute_value(x::NumFieldElem, p::InfPlc, prec::Int = 32) -> ArbFieldElem
```

Return the evaluation of `x` at the normalized absolute valuation contained in the infinite place. If `e` is a complex embedding inducing `p`, this is `abs(e(x))` if `e` is real and `abs(e(x))^2` otherwise.

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^3 - 2, "a");

julia> absolute_value(a, real_places(K)[1])
[1.2599210499 +/- 8.44e-11]

julia> absolute_value(a, complex_places(K)[1])
[1.587401052 +/- 6.63e-10]
```
