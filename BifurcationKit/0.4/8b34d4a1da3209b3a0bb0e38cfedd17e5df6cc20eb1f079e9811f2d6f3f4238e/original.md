TWProblem(prob, ∂::Tuple, u₀; DAE = 0, jacobian::Symbol = :AutoDiff)

This composite type implements a functional for freezing symmetries in order, for example, to compute traveling waves (TW). Note that you can freeze many symmetries, not just one, by passing many Lie generators. When you call `pb(x, par)`, it computes:

```
                ┌                   ┐
                │ f(x, par) - s⋅∂⋅x │
                │   <x - u₀, ∂⋅u₀>  │
                └                   ┘
```

## Arguments

  * `prob` bifurcation problem with continuous symmetries
  * `∂::Tuple = (T1, T2, ⋯)` tuple of Lie generators. In effect, each of these is an (differential) operator which can be specified as a (sparse) matrix or as an operator implementing `LinearAlgebra.mul!`.
  * `u₀` reference solution

## Additional Constructor(s)

```
pb = TWProblem(prob, ∂, u₀; kw...)
```

This simplified call handles the case where a single symmetry needs to be frozen.

## Useful function

  * `updatesection!(pb::TWProblem, u0)` updates the reference solution of the problem using `u0`.
  * `nb_constraints(::TWProblem)` number of constraints (or Lie generators)
