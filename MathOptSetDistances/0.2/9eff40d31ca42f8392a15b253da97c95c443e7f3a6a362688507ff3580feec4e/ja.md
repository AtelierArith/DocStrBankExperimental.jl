```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.DualExponentialCone) where {T}
```

ベクトル `v` の双対指数円錐への射影の導関数、すなわち `Kexp^* = {(u,v,w) | u < 0, -u*exp(v/u) <= exp(1)*w } U {(u,v,w)| u == 0, v >= 0, w >= 0}`。

参考文献：

  * [Solution Refinement at Regular Points of Conic Problems]

(https://stanford.edu/~boyd/papers/cone*prog*refine.html) by Enzo Busseti, Walaa M. Moursi, and Stephen Boyd
