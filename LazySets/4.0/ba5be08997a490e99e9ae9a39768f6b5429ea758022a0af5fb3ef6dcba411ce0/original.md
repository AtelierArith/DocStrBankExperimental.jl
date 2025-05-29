```
CartesianProduct{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

Type that represents the Cartesian product of two sets, i.e., the set

$$
Z = \{ z ∈ ℝ^{n + m} : z = (x, y),\qquad x ∈ X, y ∈ Y \}.
$$

If $X ⊆ ℝ^n$ and $Y ⊆ ℝ^m$, then $Z$ is $n+m$-dimensional.

### Fields

  * `X` – first set
  * `Y` – second set

### Notes

See also [`CartesianProductArray`](@ref) for an implementation of a Cartesian product of more than two sets.

The `EmptySet` is the almost absorbing element for `CartesianProduct` (except that the dimension is adapted).

The Cartesian product preserves convexity: if the set arguments are convex, then their Cartesian product is convex as well.

In some docstrings the word "block" is used to denote each wrapped set, with the natural order, i.e. we say that the first block of a Cartesian product `cp` is `cp.X` and the second block is `cp.Y`.

### Examples

The Cartesian product of two sets `X` and `Y` can be constructed either using `CartesianProduct(X, Y)` or the short-cut notation `X × Y` (to enter the *times* symbol, write `\times<tab>`).

```jldoctest cartesianproduct_constructor
julia> I1 = Interval(0, 1);

julia> I2 = Interval(2, 4);

julia> I12 = I1 × I2;

julia> typeof(I12)
CartesianProduct{Float64, Interval{Float64}, Interval{Float64}}
```

A hyperrectangle is the Cartesian product of intervals, so we can convert `I12` to a `Hyperrectangle` type:

```jldoctest cartesianproduct_constructor
julia> convert(Hyperrectangle, I12)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([0.5, 3.0], [0.5, 1.0])
```
