```
choInv(P::AbstractArray{T};
	kind::Symbol = :LLt, tol::Real = √eps(T)) where T<:RealOrComplex
```

For a real or complex positive definite matrix $P$, let $P=LL^H$ be its  *Cholesky decomposition* and $P=L_1DL_1^H$ the related *LDLt* decomposition.  In the above, $L$ is a lower triangular matrix, $D$ a positive-definite  diagonal matrix and $L_1$ a unit lower triangular matrix.  Return:

  * if `kind`is `:LLt` (default), the 2-tuple $L$, $L^{-H}$
  * if `kind`is `:LDLt`, the 3-tuple $L_1$, $D$, $L_1^{-H}$.

Those are obtained in one pass and for small matrices this is faster  then calling Julia's  [chelosky](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.cholesky)  function and inverting the lower factor unless you set

```
 BLAS.set_num_threads(1).
```

Input matrix `P` may be of type `Matrix` or `Hermitian`. Since only the  lower triangle is used, `P` may also be a `LowerTriangular` view of a  positive definite matrix.  If `P` is real, it can also be of the `Symmetric` type.

The algorithm is a *multiplicative Gaussian elimination*.  If run completely, in input matrix `P` there will be the Identity at the end.

**Notes:**  Output $L^{-H}$ is an inverse square root (whitening matrix) of $P$,  since $L^{-1}PL^{-H}=I$. It therefore yields the inversion of $P$ as  $P^{-1}=L^{-H}L^{-1}$. It is the fastest whitening matrix to be computed,  however it yields poor numerical precision, especially for large matrices.

The following relations holds:

  * $L=PL^{-H}$
  * $L^{H}=L^{-1}P$
  * $L^{-H}=P^{-1}L$
  * $L^{-1}=L^{H}P^{-1}$.

We also have

  * $L^{H}L=L^{-1}P^{2}L^{-H}=UPU^H$, with $U$ orthogonal (see below) and
  * $L^{-1}L^{-H}=L^{H}P^{-2}L=UP^{-1}U^H$.

$LL^{H}$ and $L^{H}L$ are unitarily similar, that is,

$ULL^{H}U^H=L^{H}L$,

where $U=L^{-1}P^{1/2}$, with $P^{1/2}=H$ the *principal*  (unique symmetric) square root of $P$. This is seen writing  $PP^{-1}=HHL^{-H}L^{-1}$; multiplying both sides on the left by $L^{-1}$  and on the right by $L$ we obtain

$L^{-1}PP^{-1}L=L^{-1}HHL^{-H}=I=(L^{-1}H)(L^{-1}H)^H$

and since $L^{-1}H$ is square it must be unitary.

From these expressions we have

  * $H=LU=U^HL^H$
  * $L=HU^H$
  * $H^{-1}=U^HL^{-1}$
  * $L^{-1}=UH^{-1}$.

$U$ is the *polar factor* of $L^{H}$, *i.e.*, $L^{H}=UH$,  since $LL^{H}=HU^HUH^H=H^2=P$.

From $L^{H}L=UCU^H$ we have $L^{H}LU=UC=ULL^{H}$ and from  $U=L^{-1}H$ we have $L=HU^H$.

**See also**: [`choInv!`](@ref), [`choL`](@ref).

**Examples**

```julia
using PosDefManifold
n, t = 800, 6000
etol = 1e-9
Z=randn(t, n)
Y=Z'*Z
Yi=inv(Y)

A, B=choInv!(copy(Y))
norm(A*A'-Y)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(B*B'-Yi)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

A, D, B=choInv!(copy(Y); kind=:LDLt)
norm(Y-A*D*A')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(Yi-B*inv(D)*B')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

# repeat the test for complex matrices
Z=randn(ComplexF64, t, n)
Y=Z'*Z
Yi=inv(Y)

A, B=choInv!(copy(Y))
norm(A*A'-Y)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(B*B'-Yi)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

A, D, B=choInv!(copy(Y); kind=:LDLt)
norm(Y-A*D*A')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(Yi-B*inv(D)*B')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
```
