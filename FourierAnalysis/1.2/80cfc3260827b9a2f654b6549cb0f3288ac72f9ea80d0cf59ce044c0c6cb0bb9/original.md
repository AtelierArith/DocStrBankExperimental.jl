```julia
(1)
function polar(c::Complex)

(2)
function polar(Z::AbstractArray{T}) where T<:Complex

(3)
function polar(Z::TFAnalyticSignal)

```

(1)

Return the amplitude (modulus) and phase (argument) of a complex number as a 2-tuple.

(2)

Return the amplitude and phase of a complex array `Z`. Typically, `Z` holds analytic signal, in which case return the analytic (instantaneous) amplitude and phase. The output is a tuple of two real arrays of the same size as data field `Z.y`.

(3)

Return the analytic (instantaneous) amplitude and phase of the [TFAnalyticSignal](@ref) object `Z`. The output is a tuple of two real arrays of the same size as data field `Z.y`.

~

In all methods the phase is returned in [−π, π].

**See**: [`amplitude`](@ref), [`phase`](@ref), [TFAnalyticSignal](@ref).

**Examples**: see examples of [`amplitude`](@ref).
