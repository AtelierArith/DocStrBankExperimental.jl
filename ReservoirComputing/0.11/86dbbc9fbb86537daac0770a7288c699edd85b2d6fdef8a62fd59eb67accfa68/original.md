```
StandardStates()
```

When this struct is employed, the states of the reservoir are not modified.

# Example

```jldoctest
julia> states = StandardStates()
StandardStates()

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
