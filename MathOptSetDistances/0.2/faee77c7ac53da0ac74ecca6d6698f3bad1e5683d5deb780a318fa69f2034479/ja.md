```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.ExponentialCone) where {T}
```

ベクトル `v` の指数円錐の閉包への射影の導関数、すなわち `cl(Kexp) = {(x,y,z) | y e^(x/y) <= z, y>0 } U {(x,y,z)| x <= 0, y = 0, z >= 0}`。

参考文献:

  * [Solution Refinement at Regular Points of Conic Problems](https://stanford.edu/~boyd/papers/cone_prog_refine.html)

Enzo Busseti、Walaa M. Moursi、Stephen Boyd 著
