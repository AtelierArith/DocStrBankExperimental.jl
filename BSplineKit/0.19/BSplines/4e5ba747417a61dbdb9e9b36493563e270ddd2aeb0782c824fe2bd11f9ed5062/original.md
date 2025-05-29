```
BSplineBasis{k, T}
```

B-spline basis for splines of order `k` and knot element type `T <: Real`.

The basis is defined by a set of knots and by the B-spline order.

---

```
BSplineBasis(order::BSplineOrder{k}, ts::AbstractVector; augment = Val(true))
BSplineBasis(order::BSplineOrder{k}, ts::NTuple; augment = Val(true))
```

Create B-spline basis of order `k` with breakpoints `ts`.

If `augment = Val(true)`, breakpoints will be "augmented" so that boundary knots have multiplicity `k`. Note that, if they are passed as a regular `Vector`, the input may be modified. See [`augment_knots!`](@ref) for details.

# Examples

```jldoctest BSplineBasis
julia> breaks = range(-1, 1; length = 21)
-1.0:0.1:1.0

julia> B = BSplineBasis(BSplineOrder(5), breaks)
24-element BSplineBasis of order 5, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5  …  0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0, 1.0]
```

Note that first and last knots are repeated $k = 5$ times.

If `augment = Val(false)`, input breakpoints are taken without modification as the knots $t_i$ of the B-spline basis. Note that the valid domain is reduced to $[-0.6, 0.6]$. The domain is always defined as the range $[t_k, t_{N + 1}]$, where $N$ is the length of the basis (below, $N = 16$).

```jldoctest BSplineBasis
julia> Bn = BSplineBasis(5, breaks, augment = Val(false))
16-element BSplineBasis of order 5, domain [-0.6, 0.6]
 knots: -1.0:0.1:1.0
```

# Statically-sized bases

To define a basis with static size (i.e. size known at compile time), the breakpoints `ts` should be passed as a tuple or as an `SVector` (from the `StaticArrays` package):

```jldoctest
julia> breaks = (0.0, 0.1, 0.2, 0.6, 1.0);

julia> B = BSplineBasis(BSplineOrder(3), breaks)
6-element BSplineBasis of order 3, domain [0.0, 1.0]
 knots: [0.0, 0.0, 0.0, 0.1, 0.2, 0.6, 1.0, 1.0, 1.0]

julia> knots(B)
9-element StaticArraysCore.SVector{9, Float64} with indices SOneTo(9):
 0.0
 0.0
 0.0
 0.1
 0.2
 0.6
 1.0
 1.0
 1.0
```
