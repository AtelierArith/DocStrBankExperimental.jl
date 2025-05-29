```
@add_predicate qc desc pred
```

Add the predicate `pred` to the set of tests `qc` with description `desc`.

# Arguments

  * `qc`: object of type [`Quickcheck`](@ref Quickcheck)
  * `desc`: string describing the predicate
  * `pred`: predicate in the form of an [anonymous function](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions)

# Notes

The form of `pred` is very strict:

  * It has to be an anonymous function. Formally, it should be an `Expr` of type `->`.
  * The type of each argument appearing on the left-hand side of `pred` has to be specified with the `x::Type` syntax.
  * The names of the arguments of `pred` matter! Specifically, in a given [`Quickcheck`](@ref Quickcheck) object, the type of every argument must be consistent across predicates (see examples).
  * Each predicate stored in a given [`Quickcheck`](@ref Quickcheck) object must be given a distinct description.

# Examples

```jldoctest
julia> qc = Quickcheck("A Test")
A Test: 0 predicate and 0 free variable.

julia> @add_predicate qc "Identity" (x::Float64 -> x == x)
A Test: 1 predicate and 1 free variable.
x::Float64

julia> @add_predicate qc "Sum commute" ((n::Int, x::Float64) -> n + x == x + n)
A Test: 2 predicates and 2 free variables:
n::Int64
x::Float64

julia> @add_predicate qc "Is odd" isodd(x)
ERROR: Predicate declaration must have the form of an anonymous function (... -> ...)
[...]

julia> @add_predicate qc "Is odd" (x::Int -> is_odd(x))
ERROR: A declaration for variable x already exists with type Float64; please choose another name for x
[...]
```
