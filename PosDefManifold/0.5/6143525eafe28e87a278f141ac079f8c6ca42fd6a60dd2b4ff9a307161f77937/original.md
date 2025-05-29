```
fidelity(P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

Given two positive definte `Hermitian` matrices $P$ and $Q$,  return their *fidelity*:

$tr\big(P^{1/2}QP^{1/2}\big)^{1/2}.$

This is used in quantum physics and is related to the  [Wasserstein](@ref) metric. See for example Bhatia, Jain and Lim (2019b)[🎓](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(5);
Q=randP(5);
f=fidelity(P, Q)
```
