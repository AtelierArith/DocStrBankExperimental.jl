```
group(iter)
group(by::Union{Function, Type}, iter)
group(by::Union{Function, Type}, f::Union{Function, Type}, iter...)
```

Return a dictionary of groups of elements `x` of the iterable `iter` into groups labeled by `by(x)`, transforming each element to `f(x)`, where `by` and `f` default to the `identity` function. If multiple collections (of the same length) are provided, the transformations `by` and `f` occur elementwise.

# Example

```jldoctest
julia> group(iseven, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
Dictionary{Bool,Array{Int64,1}} with 2 entries:
 false │ [1, 3, 5, 7, 9]
 true  │ [2, 4, 6, 8, 10]

julia> group(iseven, x -> x ÷ 2, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
Dictionary{Bool,Array{Int64,1}} with 2 entries:
 false │ [0, 1, 2, 3, 4]
 true  │ [1, 2, 3, 4, 5]
```
