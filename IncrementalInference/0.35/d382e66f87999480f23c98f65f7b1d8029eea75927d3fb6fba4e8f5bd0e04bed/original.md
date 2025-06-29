```julia
mutable struct FactorGradientsCached!{F<:DistributedFactorGraphs.AbstractRelative, S, M, P, G, L}
```

Container for calculating gradients on a factor.  See helper contructor functions.

Take graph on one function $f$ between two variables and based on measurement $z$

```
(:x1)-[:x1x2f1]-(:x2)
```

The gradient (a matrix operating on coordinates) is defined as $(▽f - I)$ according to

$$
0 = (▽ f - I) dC
$$

where the augmented vector of coordinates is $dC = [dX_1, dX_2]'$.  The idea is that $dC$ should be  in the null space of $(▽f - I)$ as per normal partial derivative (vector) decomposition;

$$
dX_1 = {∂f}/{∂X_2'} dX_2 + ...
$$

modeled in coordinates.

Notes

  * Memory is cached in the object.
  * Gradients are updated as a functor call to the object, see example.
  * The factor is assumed to be in "tension or compression" which manifests as `_slack` in the calculated factor residual which is also cached.

DevNotes

  * TODO type stability
  * TODO in-place memory operations
  * TODO relax hard coordinate assumptions and instead allow direct operator definitions with the manifold tangent $T_f M$.

Example

```julia
# problem set
pp = LinearRelative(MvNormal([10;0],[1 0; 0 1]))
measurement = ([10.0;0.0],)
varTypes = (ContinuousEuclid{2}, ContinuousEuclid{2})
pts = ([0;0.0], [9.5;0])

# build and evaluate the functor object
grad = FactorGradientsCached!(pp, varTypes, measurement, pts);
J = grad(measurement..., pts...)

# cached value stored
J_ = grad.cached_gradients

# double check things are working
@assert norm(J_ - J) < 1e-6 
```

Related

[`calcFactorResidualTemporary`](@ref), [`_buildGraphByFactorAndTypes`](@ref)
