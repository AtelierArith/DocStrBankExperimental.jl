```
partial_to_adolc_format(partial::Vector{I_1}, degree::I_2) where {I_1<:Integer, I_2<:Integer}
```

Transforms a given `partial` to the [ADOLC-Format](@ref). 

!!! note
    `partial` is required to be in the `Partial-format`


# Example:

```jldoctest

partial = [1, 0, 4]
degree = sum(partial)
partial_to_adolc_format(partial, degree)

# output

5-element Vector{Int32}:
 3
 3
 3
 3
 1
```
