```
DecodeResult(
    success::Union{Nothing,Bool},
    recovery::Union{Nothing,AbstractVector{Bool}},
    logical_commutations::Union{Nothing,AbstractVector{Bool}}
    custom_values::Union{Nothing,AbstractVector}
)
DecodeResult(;
    success::Union{Nothing,Bool}=nothing,
    recovery::Union{Nothing,AbstractVector{Bool}}=nothing,
    logical_commutations::Union{Nothing,AbstractVector{Bool}}=nothing
    custom_values::Union{Nothing,AbstractVector}=nothing
)
```

Construct a decoding result as returned by [`decode`](@ref).

Typically decoders will provide a `recovery` operation and delegate the evaluation of `success` and `logical_commutations` to the client, e.g. [`App`](@ref App). Optionally, `success` and/or `logical_commutations` may be provided as overrides. At least one of `recovery` or `success` must be specified to allow a success value to be resolved. Additionally `custom_values` may be specified. If `logical_commutations` and/or `custom_values` are provided then they should be of consistent type and size over identically parameterized simulation runs. For example, [`App`](@ref App) will sum `logical_commutations` across runs and, similarly, if `custom_values` are numbers they will be summed across runs, and if they are arrays they will be concatenated using `vcat`.

See also [`decode`](@ref).

# Examples

```jldoctest
julia> DecodeResult(; recovery=BitVector([1, 0, 1, 0, 1, 1]))  # typical use-case
DecodeResult{Nothing}(nothing, Bool[1, 0, 1, 0, 1, 1], nothing, nothing)

julia> DecodeResult(; success=true)  # override success
DecodeResult{Nothing}(true, nothing, nothing, nothing)

julia> DecodeResult(; success=false, logical_commutations=BitVector([1, 0]))  # override all
DecodeResult{Nothing}(false, nothing, Bool[1, 0], nothing)

julia> DecodeResult(; success=true, custom_values=[2.3, 4.1])  # custom values (numbers)
DecodeResult{Vector{Float64}}(true, nothing, nothing, [2.3, 4.1])

julia> DecodeResult(; success=true, custom_values=[[2.3], [4.1]])  # custom values (arrays)
DecodeResult{Vector{Vector{Float64}}}(true, nothing, nothing, [[2.3], [4.1]])

julia> DecodeResult(true, nothing, nothing, [2.3, 4.1])  # positional parameters
DecodeResult{Vector{Float64}}(true, nothing, nothing, [2.3, 4.1])

julia> DecodeResult(; success=nothing, recovery=nothing)  # too few specified parameters
ERROR: QecsimError: at least one of 'success' or 'recovery' must be specified
Stacktrace:
[...]
```
