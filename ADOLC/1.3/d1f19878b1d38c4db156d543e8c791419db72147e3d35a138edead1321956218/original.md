```
partial_to_adolc_format!(res::Vector{Cint}, partial::Vector{I_1}, degree::I_2) where {I_1<:Integer, I_2<:Integer}
partial_to_adolc_format!(res::Vector{Cint}, partial::Vector{Cint}, degree::I) where I <: Integer
```

Variant of [`partial_to_adolc_format`](@ref) that writes the result to `res`.

# Example:

```jldoctest
partial = [1, 3, 2, 0]
degree = sum(partial)
res = zeros(Int32, degree)
partial_to_adolc_format!(res, partial, degree)

# output

6-element Vector{Int32}:
 3
 3
 2
 2
 2
 1
```
