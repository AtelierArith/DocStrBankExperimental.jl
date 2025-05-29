`torus(m::AbstractMatrix)`

`m`  should be a matrix of finite order. The function returns the coset `T` of  the  trivial  group  such  that  `T.F==m`.  When  `m`  is  integral his corresponds to an algebraic torus `𝐓` of rank `size(m,1)`, with an isogeny which acts by `m` on `X(𝐓)`.

```julia-repl
julia> torus([0 -1;1 -1])
Φ₃
```
