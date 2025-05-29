```julia
(1)
function unwrapPhase(Z::AbstractArray{T};
                                unwrapdims::Int=0) where T<:Complex

(2)
function unwrapPhase(ϴ::AbstractArray{T};
                                unwrapdims::Int=0) where T<:Real

(3)
unwrapPhase(ϴ::TFPhase) [constructor of a TFPhase object]

(4)
unwrapPhase(𝚯::TFPhaseVector) [constructor of a TFPhaseVector object]
```

(1)

If optional keyword argument `unwrapdims` is > 0, compute the phase (argument) from a *complex* array and unwrap it along the `unwrapdims` dimension, otherwise (default) return `Z`. Typically, `Z` holds analytic signal.

(2)

If optional keyword argument `unwrapdims` is > 0, unwrap along the `unwrapdims` dimension a *real* array holding phase data in [−π, π], otherwise return `ϴ`.

(3)

Construct a [TFPhase](@ref) object by unwrapping its phase along the time dimension and copying all other fields from the `ϴ` object. If `ϴ.func` is different from the `identity` (do nothing) function, return instead an error message.

(4)

As (3), but conctruct a [TFPhaseVector](@ref) holding [TFPhase](@ref) objects in 𝚯 with the phase unwrapped. `ϴ.func` must be the identity function for all ϴ ∈ 𝚯.

The unwrapped phase is defined as the cumulative sum of the phase (along the relevant dimension) once this is represented in [0, 2π].

**Examples**: see examples of [`amplitude`](@ref).
