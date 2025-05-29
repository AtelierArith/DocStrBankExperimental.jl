```
IntervalMatrix{T, IT, MT<:AbstractMatrix{IT}} <: AbstractIntervalMatrix{IT}
```

An interval matrix i.e. a matrix whose coefficients are intervals. This type is parametrized in the number field, the interval type, and the matrix type.

### Fields

  * `mat` – matrix whose entries are intervals

### Examples

```jldoctest
julia> A = IntervalMatrix([-1 .. -0.8 0 .. 0; 0 .. 0 -1 .. -0.8])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, -0.7999999]   [0.0, 0.0]
  [0.0, 0.0]         [-1.0, -0.7999999]
```

An interval matrix proportional to the identity matrix can be built using the `UniformScaling` operator from the standard library `LinearAlgebra`. For example,

```jldoctest interval_uniform_scaling
julia> using LinearAlgebra

julia> IntervalMatrix(interval(1)*I, 2)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [1.0, 1.0]  [0.0, 0.0]
 [0.0, 0.0]  [1.0, 1.0]
```

The number of columns can be specified as a third argument, creating a rectangular $m × n$ matrix such that only the entries in the main diagonal, $(1, 1), (2, 2), …,  (k, k)$ are specified, where $k = \min(m, n)$:

```jldoctest interval_uniform_scaling
julia> IntervalMatrix(interval(-1, 1)*I, 2, 3)
2×3 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, 1.0]   [0.0, 0.0]  [0.0, 0.0]
  [0.0, 0.0]  [-1.0, 1.0]  [0.0, 0.0]

julia> IntervalMatrix(interval(-1, 1)*I, 3, 2)
3×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, 1.0]   [0.0, 0.0]
  [0.0, 0.0]  [-1.0, 1.0]
  [0.0, 0.0]   [0.0, 0.0]
```

An uninitialized interval matrix can be constructed using `undef`:

```jldoctest undef_test
julia> m = IntervalMatrix{Float64}(undef, 2, 2);

julia> typeof(m)
IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}
```

Note that this constructor implicitly uses a dense matrix, `Matrix{Float64}`, as the matrix (`mat`) field in the new interval matrix.
