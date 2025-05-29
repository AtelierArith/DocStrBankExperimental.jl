```julia
    laplacianEigenMaps(Ω::𝕃{S}, q::Int;
    <
    tol::Real=0.,
    maxiter::Int=300,
    verbose=false >) where S<:Real
```

**alias**: `laplacianEM`

Given the lower triangular part of a Laplacian $Ω$ (see [`laplacian`](@ref) ) return the *eigen maps* in $q$ dimensions, i.e., the $q$ eigenvectors of the Laplacian associated with the largest $q$ eigenvalues, excluding the first (which is always equal to 1.0). The eigenvectors are of the same type as $Ω$. They are all divided element-wise by the first eigenvector (see Lafon, 2004[🎓](@ref)).

The eigenvectors of the Laplacian are computed by the power iterations+modified Gram-Schmidt method (see [`powerIterations`](@ref)), allowing the execution of this function for Laplacian matrices of very large size.

Return the 4-tuple $(Λ, U, iterations, convergence)$, where:

  * $Λ$ is a $q⋅q$ diagonal matrix holding on diagonal the eigenvalues corresponding to the $q$ dimensions of the Laplacian eigen maps,
  * $U$ holds in columns the $q$ eigenvectors holding the $q$ coordinates of the points in the embedding space,
  * $iterations$ is the number of iterations executed by the power method,
  * $convergence$ is the convergence attained by the power method.

Using the notion of Laplacian, spectral embedding seek a low-dimension representation of the data emphasizing local neighbothood information while neglecting long-distance information. The embedding is non-linear, however the embedding space is Euclidean. The eigenvectors of $U$ holds the coordinates of the points in the embedding space (typically two- or three-dimensional for plotting or more for clustering). Spectral embedding is done for plotting data in low-dimension, clustering, imaging, classification, following their trajectories over time or other dimensions, and much more. For examples of applications see Ridrigues et *al.* (2018) [🎓](@ref) and references therein.

**Arguments**:

  * $Ω$ is a real `LowerTriangular` normalized Laplacian obtained by the [`laplacian`](@ref) function,
  * $q$ is the dimension of the Laplacian eigen maps;
  * The following are *<optional keyword arguments>* for the power iterations:
  * `tol` is the tolerance for convergence (see below),
  * `maxiter` is the maximum number of iterations allowed,
  * if `verbose` is true, the convergence at all iterations will be printed.

!!! note "Nota Bene"
    The maximum value of $q$ that can be requested is $n-1$, where $n$ is the size of the Laplacian. In general, $q=2$ or $q=3$ is requested.

    $tol$ defaults to the square root of `Base.eps` of the (real) type of $Ω$. This corresponds to requiring equality for the convergence criterion over two successive power iterations of about half of the significant digits.


**See also**: [`distanceSqrMat`](@ref), [`laplacian`](@ref), [`spectralEmbedding`](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of 4 random 10x10 SPD matrices
Pset=randP(10, 4)
Δ²=distanceSqrMat(Fisher, Pset)
Ω=laplacian(Δ²)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2; verbose=true)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2; verbose=true, maxiter=500)
```
