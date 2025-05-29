```julia
    matP(ς::Vector{T}) where T<:RealOrComplex
```

*Matrizize* a tangent vector (vector) ς :  vec -> mat.

This is the function reversing the [`vecP`](@ref) function, thus the weighting applied therein is reversed as well.

If $ς=vecP(S)$ and $S$ is a $n⋅n$ Hermitian or Symmetric matrix, $ς$  is a tangent vector of size $n(n+1)/2$. The result of calling `matP(ς)` is then $n⋅n$ matrix $S$. $S$ is always returned flagged as `Hermitian`.

**To Do**: This function may be rewritten more efficiently.

**Examples**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
G=mean(Fishr, P, Q)
# projecting P at onto the tangent space at the Fisher mean base point
S=logMap(Fisher, P, G)
# vectorize S
v=vecP(S)
# Rotate the vector by an orthogonal matrix
n=Int(size(S, 1)*(size(S, 1)+1)/2)
U=randP(n)
z=U*v
# Get the point in the tangent space
S=matP(z)
```
