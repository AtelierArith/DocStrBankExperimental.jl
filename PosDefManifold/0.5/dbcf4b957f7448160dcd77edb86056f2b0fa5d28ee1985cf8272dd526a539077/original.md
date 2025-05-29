```julia
    laplacian(Δ²::𝕃{S}, epsilon::Real=0;
              <densityInvariant=false>) where S<:Real
```

Given a `LowerTriangular` matrix of squared inter-distances $Δ^2$, return the lower triangular part of the so-called *normalized Laplacian* or *density-invariant normalized Laplacian*, which in both cases is a symmetric Laplacian. The elements of the Laplacian are of the same type as the elements of $Δ^2$. The result is a `LowerTriangular` matrix.

The definition of Laplacian given by Lafon (2004)[🎓](@ref) is implemented:

First, a [Gaussian radial basis functions](https://bit.ly/1HVyf55), known as *Gaussian kernel* or *heat kernel*, is applied to all elements of $Δ^2$, such as

$W_{ij} = exp\bigg(\frac{\displaystyle{-Δ^2_{ij}}}{\displaystyle{2ε}}\bigg)$,

where $ε$ is the *bandwidth* of the kernel.

If <optional keyword argument> `densityInvariant=true` is used, then the density-invariant transformation is applied

$W \leftarrow E^{-1}WE^{-1}$

where $E$ is the diagonal matrix holding on the main diagonal the sum of the rows (or columns) of $W$.

Finally, the normalized Laplacian (density-invariant or not) is defined as

$Ω = D^{-1/2}WD^{-1/2}$,

where $D$ is the diagonal matrix holding on the main diagonal the sum of the rows (or columns) of $W$.

If you do not provide argument `epsilon`, the bandwidth $ε$ is set to the median of the elements of squared distance matrix $Δ^2_{ij}$. Another educated guess is the dimension of the original data, that is, the data that has been used to compute the squared distance matrix. For positive definite matrices this is $n(n-1)/2$, where $n$ is the dimension of the matrices. Still another is the dimension of the ensuing [`spectralEmbedding`](@ref) space. Keep in mind that by tuning the `epsilon` parameter (which must be positive) you can control both the rate of compression of the embedding space and the spread of points in the embedding space. See Coifman et *al.* (2008)[🎓](@ref) for a discussion on $ε$.

!!! note "Nota Bene"
    The Laplacian as here defined can be requested for any input matrix of squared inter-distances, for example, those obtained on scalars or on vectors using appropriate metrics. In any case, only the lower triangular part of the Laplacian is taken as input. See [typecasting matrices](@ref).


**See also**: [`distanceSqrMat`](@ref), [`laplacianEigenMaps`](@ref), [`spectralEmbedding`](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of 4 random 10x10 SPD matrices
Pset=randP(10, 4) # or, using unicode: 𝐏=randP(10, 4)
Δ²=distanceSqrMat(Fisher, Pset)
Ω=laplacian(Δ²)

# density-invariant Laplacian
Ω=laplacian(Δ²; densityInvariant=true)

# increase the bandwidth
r=size(Δ², 1)
myεFactor=0.1
med=Statistics.median([Δ²[i, j] for j=1:r-1 for i=j+1:r])
ε=2*myεFactor*med
Ω=laplacian(Δ², ε; densityInvariant=true)
```
