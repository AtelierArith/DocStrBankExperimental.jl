```
cayley(Y::Manifold, Δ)
```

Take as input an element of a manifold `Y` and a tangent vector in `Δ` in the corresponding tangent space and compute the Cayley retraction.

In different notation: take as input an element $x$ of $\mathcal{M}$ and an element of $T_x\mathcal{M}$ and return $\mathrm{Cayley}(v_x).$ 

# Examples

```jldoctest
using GeometricMachineLearning

Y = StiefelManifold([1. 0. 0.;]' |> Matrix)
Δ = [0. .5 0.;]' |> Matrix
Y₂ = cayley(Y, Δ)

Y₂' * Y₂ ≈ [1.;]

# output

true
```

See the example in [`geodesic(::Manifold{T}, ::AbstractMatrix{T}) where T`].
