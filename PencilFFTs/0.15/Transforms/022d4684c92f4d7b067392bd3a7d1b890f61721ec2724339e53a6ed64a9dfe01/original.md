```
scale_factor(transform::AbstractTransform, A, [dims = 1:ndims(A)])
```

Get factor required to normalise the given array after a transformation along dimensions `dims` (all dimensions by default).

The array `A` must have the dimensions of the transform input.

**Important**: the dimensions `dims` must be the same that were passed to [`plan`](@ref).

# Examples

```jldoctest scale_factor
julia> C = zeros(ComplexF32, 3, 4, 5);

julia> scale_factor(Transforms.FFT(), C)
60

julia> scale_factor(Transforms.BFFT(), C)
60

julia> scale_factor(Transforms.BFFT(), C, 2:3)
20

julia> R = zeros(Float64, 3, 4, 5);

julia> scale_factor(Transforms.RFFT(), R, 2)
4

julia> scale_factor(Transforms.RFFT(), R, 2:3)
20

julia> scale_factor(Transforms.BRFFT(8), C)
96

julia> scale_factor(Transforms.BRFFT(9), C)
108
```

This will fail because the input of `RFFT` is real, and `R` is a complex array:

```jldoctest scale_factor
julia> scale_factor(Transforms.RFFT(), C, 2:3)
ERROR: MethodError: no method matching scale_factor(::PencilFFTs.Transforms.RFFT, ::Array{ComplexF32, 3}, ::UnitRange{Int64})
```
