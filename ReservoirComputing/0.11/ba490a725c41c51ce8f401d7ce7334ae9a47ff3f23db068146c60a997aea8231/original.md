```
PaddedExtendedStates(padding)
PaddedExtendedStates(;padding=1.0)
```

Constructs a `PaddedExtendedStates` struct, which first extends the reservoir states with training or prediction data,then pads them with a specified value (defaulting to 1.0).

# Example

```jldoctest
julia> states = PaddedExtendedStates(1.0)
PaddedExtendedStates{Float64}(1.0)

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec, fill(3.0f0, 3))
9-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0
 1.0
 3.0
 3.0
 3.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat, fill(3.0f0, 3))
9×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 1.0  1.0  1.0  1.0  1.0
 3.0  3.0  3.0  3.0  3.0
 3.0  3.0  3.0  3.0  3.0
 3.0  3.0  3.0  3.0  3.0
```
