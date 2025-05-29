```
function ParamDict(type)
    Union{Dict{String, Array{T}}, Dict{String, Vector{T}}} where T <: type
end
```

Type constructor for Dictionary of model parameters to be passed to derivative functions by name.  This allows one to pass both vector parameters (and scalars written as vectors), as well as matrix valued parameters such as diffusion arrays.
