```
load(io)
```

Load a collection of failed test cases serialized by a [`@quickcheck`](@ref) run.  Argument `io` can be of type `IO`, `AbstractString` or `AbstractPath`.

# Examples

```jldoctest
julia> ft = JCheck.load("JCheck_test.jchk")
2 failing predicates:
Product commute
Is odd
```
