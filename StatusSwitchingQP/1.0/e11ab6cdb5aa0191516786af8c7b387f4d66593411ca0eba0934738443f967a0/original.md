```
    QP(V::Matrix{T}; q, u, d, G, g, A, b) where T
    QP(P::QP{T}, q::Vector{T}, L::T=0.0) where T
    QP(P::QP{T}, mu::T, q::Vector{T}) where T
```

Setup a quadratic programming model:

$$
    min   (1/2)z′Vz+q′z
    s.t.   Az=b ∈ R^{M}
           Gz≤g ∈ R^{J}
           d≤z≤u ∈ R^{N}
$$

variable z[i] may be free, say d[i]= -Inf and u[i]=+Inf . No equalities if M=0. Default values: q = 0, u = +∞, d = 0, G = [], g = [], A = ones(1,N), b = [1], such that

$$
    min   (1/2)z′Vz
    s.t.   1'z=1  ∈ R^{M}
           z≥0    ∈ R^{N}
$$

`QP(P::QP, q, L)`  :  replace the q'z term in the objective function by `-L * q` `QP(P::QP, mu, c)` :  add c'z=mu to the last row of Az=b, and remove q'z in the objective function

See also [`LP`](@ref), [`Settings`](@ref), [`solveQP`](@ref)
