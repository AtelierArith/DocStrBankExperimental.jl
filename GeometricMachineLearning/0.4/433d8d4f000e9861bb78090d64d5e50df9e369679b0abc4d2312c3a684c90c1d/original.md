```
rgrad(Y::GrassmannManifold, ∇L::AbstractMatrix)
```

Compute the Riemannian gradient for the Grassmann manifold at `Y` based on `∇L`.

Here $Y$ is a representation of $\mathrm{span}(Y)\in{}Gr(n, N)$ and $\nabla{}L\in\mathbb{R}^{N\times{}n}$ is the Euclidean gradient. 

This gradient has the property that it is orthogonal to the space spanned by $Y$.

The precise form of the mapping is: 

$$
\mathtt{rgrad}(Y, \nabla{}L) \mapsto \nabla{}L - YY^T\nabla{}L.
$$

Note the property $Y^T\mathrm{rgrad}(Y, \nabla{}L) = \mathbb{O}.$

Also see [`rgrad(::StiefelManifold, ::AbstractMatrix)`](@ref).

# Examples

```jldoctest
using GeometricMachineLearning

Y = GrassmannManifold([1 0 ; 0 1 ; 0 0; 0 0])
Δ = [1 2; 3 4; 5 6; 7 8]
rgrad(Y, Δ)

# output

4×2 Matrix{Int64}:
 0  0
 0  0
 5  6
 7  8
```
