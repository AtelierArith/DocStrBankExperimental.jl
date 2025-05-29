```julia
    vecP(S::Union{ℍ{T}, Symmetric{R}};
         range::UnitRange=1:size(S, 2)) where T<:RealOrComplex where R<:Real =
```

*Vectorize* a tangent vector (which is an `Hermitian` or `Symmetric` matrix) $S$:  mat ↦ vec.

It gives weight $1$ to diagonal elements and $√2$ to off-diagonal elements so as to preserve the norm (Barachant et *al.*, 201E)[🎓](@ref), such as

$∥S∥_F=∥vecP(S)∥_F$.

The result is a vector holding $n(n+1)/2$ elements, where $n$ is the size of $S$.

$S$ must be flagged as `Hermitian` or `Symmetric`. See [typecasting matrices](@ref).

The reverse operation is provided by [`matP`](@ref), which always return an `Hermitian` matrix.

If an optional keyword argument `range` is provided, the vectorization concerns only the rows (or columns, since the input matrix is symmetric or Hermitian) in the range. Note that in this case the operation cannot be reverted by the [`matP`](@ref), that is, in this case the matrix is 'stuck' in the tangent space.

**Examples**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# projecting P at the base point given by the geometric mean of P and Q
S=logMap(Fisher, P, G)
# vectorize S
v=vecP(S)
# vectorize onlt the first two columns of S
v=vecP(S; range=1:2)
```
