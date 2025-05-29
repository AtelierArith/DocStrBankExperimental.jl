```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, cone::MOI.PositiveSemidefiniteConeTriangle) where {T}
```

ベクトル `v` の正半定値円錐への射影の導関数、すなわち K = S^n⨥

参考文献:

  * [Proximal Algorithms](https://doi.org/10.1561/2400000003), セクション 6.3.3, p. 189
