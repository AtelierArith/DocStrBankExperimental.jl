```
PaddedStates(padding)
PaddedStates(;padding=1.0)
```

Creates an instance of the `PaddedStates` struct with specified padding value (default 1.0). The states of the reservoir are padded by vertically concatenating the padding value.

# Example

```jldoctest
julia> states = PaddedStates(1.0)
PaddedStates{Float64}(1.0)

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec)
6-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0
 1.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat)
6×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 1.0  1.0  1.0  1.0  1.0
```
