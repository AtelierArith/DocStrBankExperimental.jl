```
(1) randUnitaryMat(n::Int)
(2) randUnitaryMat(::Type{Complex{T}}, n::Int)
```

**aliases**: `randOrthMat`, `randU`

Generate a random $n⋅n$

  * (1) [orthogonal](https://bit.ly/2vrr0wU) matrix (real)
  * (2) [unitary](https://bit.ly/2JCHbmC) matrix (complex)

The matrices are generated running the modified (stabilized)  [Gram-Schmidt orthogonalization](https://bit.ly/2YE6zvy)  procedure ([`mgs`](@ref)) on an $n⋅n$ matrix filled with random Gaussian elements.

**See also**: `randΛ` ([`randEigvals`](@ref)), `randP` ([`randPosDefMat`](@ref)).

**Examples**

```julia
using PosDefManifold
n=3;
X=randU(n)*sqrt(randΛ(n))*randU(n)'  # (1) generate a random square real matrix

U=randU(ComplexF64, n);
V=randU(ComplexF64, n);
Y=U*sqrt(randΛ(n))*V' # (2) generate a random square complex matrix
```
