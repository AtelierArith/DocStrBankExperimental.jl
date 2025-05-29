```
Interval{N} <: AbstractHyperrectangle{N}
```

Type representing an interval on the real line. Mathematically, it is of the form

$$
[a, b] := \{ a ≤ x ≤ b \} ⊆ ℝ.
$$

### Fields

  * `dat` – data container for the given interval

### Notes

This type relies on the [IntervalArithmetic.jl](https://juliaintervals.github.io/IntervalArithmetic.jl/stable/) library for representation of intervals and arithmetic operations.

### Examples

Unidimensional intervals are symbolic representations of a real closed interval.

We can create intervals in different ways. The simplest way is to pass a pair of numbers:

```jldoctest interval_constructor
julia> x = Interval(0.0, 1.0)
Interval{Float64}([0, 1])
```

A 2-vector is also possible:

```jldoctest interval_constructor
julia> x = Interval([0.0, 1.0])
Interval{Float64}([0, 1])
```

An interval can also be constructed from an `IntervalArithmetic.Interval`. Note that if the package `IntervalArithmetic` is loaded in the current scope, you have to prepend the package names to `Interval`s since there is a name conflict otherwise.

```jldoctest interval_constructor
julia> using IntervalArithmetic
WARNING: using IntervalArithmetic.Interval in module Main conflicts with an existing identifier.

julia> x = LazySets.Interval(IntervalArithmetic.Interval(0.0, 1.0))
Interval{Float64}([0, 1])

julia> dim(x)
1

julia> center(x)
1-element Vector{Float64}:
 0.5
```

The usual pairwise arithmetic operators `-` and `*` are interpreted in the standard way known in interval arithmetic, so the results are `Interval`s. Note that `+` is generally used for the lazy Minkowksi sum in this library.

Intervals of other numeric types can be created as well, e.g., a rational interval:

```jldoctest interval_constructor
julia> Interval(0//1, 2//1)
Interval{Rational{Int64}}([0//1, 2//1])
```
