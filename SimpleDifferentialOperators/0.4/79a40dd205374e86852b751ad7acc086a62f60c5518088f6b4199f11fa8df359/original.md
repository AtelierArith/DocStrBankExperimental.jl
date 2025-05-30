```
extrapolatetoboundary(v, x̄, bc::Tuple{Reflecting, Reflecting})
```

Returns a `length(x̄)`-vector whose `2:(length(x̄)-1)` elements are `v`, the first and last element are extrapolated `v` on the boundaries of `x̄` according to boundary conditions `bc` given.

The first element of `bc` is applied to the lower bound, and second element of `bc` to the upper.

# Examples

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> x = interiornodes(x̄)
1
2
3

julia> v = (x -> x^2).(x)
5-element Array{Int64,1}:
  1
  4
  9
 16
 25

julia> extrapolatetoboundary(v, x̄, (Reflecting(), Reflecting()))
7-element Array{Int64,1}:
  1
  1
  4
  9
 16
 25
 25
```
