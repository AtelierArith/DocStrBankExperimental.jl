```
rgrad(Y::StiefelManifold, ∇L::AbstractMatrix)
```

Compute the Riemannian gradient for the Stiefel manifold at `Y` based on `∇L`.

Here $Y\in{}St(N,n)$ and $\nabla{}L\in\mathbb{R}^{N\times{}n}$ is the Euclidean gradient. 

The function computes the Riemannian gradient with respect to the canonical metric: [`metric(::StiefelManifold, ::AbstractMatrix, ::AbstractMatrix)`](@ref).

The precise form of the mapping is: 

$$
\mathtt{rgrad}(Y, \nabla{}L) \mapsto \nabla{}L - Y(\nabla{}L)^TY
$$

Note the property $Y^T\mathtt{rgrad}(Y, \nabla{}L)\in\mathcal{S}_\mathrm{skew}(n).$

# Examples

```jldoctest
using GeometricMachineLearning

Y = StiefelManifold([1 0 ; 0 1 ; 0 0; 0 0])
Δ = [1 2; 3 4; 5 6; 7 8]
rgrad(Y, Δ)

# output

4×2 Matrix{Int64}:
 0  -1
 1   0
 5   6
 7   8
```
