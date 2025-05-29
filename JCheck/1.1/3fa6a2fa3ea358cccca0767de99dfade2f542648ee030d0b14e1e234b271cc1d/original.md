```
@getcases ft, desc...
```

Get the predicate with description `desc` and the valuations for which it failed.

# Note

The predicate with description closest to the one given (in the sense of the Levenshtein distance) will be returned; there is no need to pass the exact description.

# Examples

```jldoctest
julia> ft = JCheck.load("JCheck_test.jchk")
2 failing predicates:
Product commute
Is odd

julia> pred, valuations = @getcases ft iod
NamedTuple{(:predicate, :valuations), Tuple{Function, Vector{Tuple}}}((Serialization.__deserialized_types__.var"#3#4"(), Tuple[(0,), (-9223372036854775808,), (6444904272543528628,)]))

julia> map(x -> pred(x...), valuations)
3-element Vector{Bool}:
 0
 0
 0
```
