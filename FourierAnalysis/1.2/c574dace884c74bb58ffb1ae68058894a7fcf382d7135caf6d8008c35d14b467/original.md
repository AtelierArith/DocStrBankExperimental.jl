```julia
(1)
function phase(z::Complex; func::Function=identity)

(2)
function phase(Z::AbstractArray{T};
                        unwrapdims::Int=0,
                        func::Function=identity) where T<:Complex

(3)
function phase(Z::TFAnalyticSignal;
                        unwrapped::Bool=false,
                        func::Function=identity)

(4)
function phase(𝐙::TFAnalyticSignalVector;
                        unwrapped::Bool=false,
                        func::Function=identity)

```

(1)

Return the phase (argument) of a complex number. This corresponds to a standard [atan2](https://en.wikipedia.org/wiki/Atan2) function. It is here provided for syntactic consistency with the following methods.

(2)

Return the phase of a complex array `Z`. Typically, `Z` holds analytic signal, in which case the output is the analytic (instantaneous) phase. The output is a real array of the same size as `Z`.

If optional keyword argument `unwrapdims` is > 0, return the unwrapped phase along the `unwrapdims` dimension of the array. For example, if `Z` is a matrix, passing `unwrapdims=1` unwrap the phase indipendently along its columns.

(3)

Return a real matrix with the analytic (instantaneous) phase of the [TFAnalyticSignal](@ref) object `Z`. The output is of the same size as the data field `Z.y`.

If optional keyword argument `unwrapped` is true, return the unwrapped phase along the time dimension of the analytic signal (dims=2).

(4)

As (3), but return a vector of phase matrices for all [TFAnalyticSignal](@ref) objects in 𝚯.

~

In all methods by default the phase is returned in [−π, π]. If a function is provided by the optional keyword argument `func`, it is applied to the phase. For example

  * passing `func=x->x+π` will return the phase in [0, 2π],
  * passing `func=x->x/π` will return the phase in [-1, 1],
  * passing `func=sin` will return the sine of the phase.

!!! note "Nota Bene"
    If in method (2) `unwrapdims` is >0 or in method (3) and (4) `unwrapped` is true, the function `func` is applied to the unwrapped phase.


**See**: [`unwrapPhase`](@ref), [TFAnalyticSignal](@ref).

**Examples**: see examples of [`amplitude`](@ref).
