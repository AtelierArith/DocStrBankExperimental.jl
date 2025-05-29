```
simple!(u,A,b;
                 abstol::Real = zero(real(eltype(b))),
                 reltol::Real = sqrt(eps(real(eltype(b)))),
                 log=false,
                 maxiter=100,
                 P=nothing
                 ) -> solution, [history]
```

単純反復スキーム $u_{i+1}= u_i - P^{-1} (A u_i -b)$ は、IterativeSolvers.jlのメソッドと似たAPIを持っています。
