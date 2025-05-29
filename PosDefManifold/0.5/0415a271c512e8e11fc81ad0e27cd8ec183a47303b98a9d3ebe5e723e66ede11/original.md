```
powerIterations(H::Union{ℍ{T}, 𝕄{T}}, q::Int;
<
evalues=false,
tol::Real=0,
maxiter::Int=300,
verbose=false>) where T<:RealOrComplex

powerIterations(L::𝕃{S}, q::Int;
< same optional keyword arguments in (1)>) where S<:Real
```

**alias**: `powIter`

(1) Compute the $q$ eigenvectors associated to the $q$ largest (real) eigenvalues  of real or complex `Hermitian` or `Matrix` $H$ using the  [power iterations](https://bit.ly/2JSo0pb) +  [Gram-Schmidt orthogonalization](https://bit.ly/2YE6zvy) as suggested by Strang.  The eigenvectors are returned with the same type as the elements of $H$.

$H$ must have real eigenvalues, that is, it must be a symmetric matrix if it is real  or an Hermitian matrix if it is complex.

(2) as in (1), but using only the `LowerTriangular` view $L$ of a matrix.  This option is available only for real matrices (see below).

The following are *<optional keyword arguments>*:

  * `tol is the tolerance for the convergence of the power method (see below),
  * `maxiter is the maximum number of iterations allowed for the power method,
  * if `verbose=true, the convergence of all iterations will be printed,
  * if `evalues=true, return the 4-tuple``(Λ, U, iterations, covergence)``,
  * if `evalues=false return the 3-tuple``(U, iterations, covergence)``.

!!! note "Nota Bene"
    Differently from the [`evd`](@ref) function, the eigenvectors and eigenvalues are sorted by decreasing order of eigenvalues.

    If $H$ is `Hermitian` and real, only its lower triangular part is used for computing the power iterations, like in (2). In this case the [BLAS.symm](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.symm) routine is used. Otherwise the [BLAS.gemm](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.gemm) routine is used. See [Threads](@ref).

    $tol$ defaults to 100 times the square root of `Base.eps` of the type of $H$. This corresponds to requiring the relative convergence criterion over two successive iterations to vanish for about half the significant digits minus 2.


**See also**: [`mgs`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# Generate an Hermitian (complex) matrix
H=randP(ComplexF64, 10);
# 3 eigenvectors and eigenvalues
U, iterations, convergence=powIter(H, 3, verbose=true)
# all eigenvectors
Λ, U, iterations, convergence=powIter(H, size(H, 2), evalues=true, verbose=true);
U'*U ≈ I && U*Λ*U'≈H ? println(" ⭐ ") : println(" ⛔ ")

# passing a `Matrix` object
Λ, U, iterations, convergence=powIter(Matrix(H), 3, evalues=true)

# passing a `LowerTriangular` object (must be a real matrix in this case)
L=𝕃(randP(10))
Λ, U, iterations, convergence=powIter(L, 3, evalues=true)
```
