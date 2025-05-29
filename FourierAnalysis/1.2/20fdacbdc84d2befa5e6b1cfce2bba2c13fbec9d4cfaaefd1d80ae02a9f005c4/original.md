```julia
(1)
function TFphase(Z :: TFAnalyticSignal;
            func      :: Function = identity,
            unwrapped :: Bool     = false)

(2)
function TFphase(𝐙 :: TFAnalyticSignalVector;
            func      ::Function = identity,
            unwrapped ::Bool     = false)

(3)
function TFphase(x         :: Vector{T},
                 sr        :: Int,
                 wl        :: Int,
                 bandwidth :: IntOrReal = 2;
           unwrapped  :: Bool         = false,
           func       :: Function     = identity,
           filtkind   :: FilterDesign = Butterworth(2),
           fmin       :: IntOrReal    = bandwidth,
           fmax       :: IntOrReal    = sr÷2,
           nonlinear  :: Bool         = false,
           fsmoothing :: Smoother     = noSmoother,
           tsmoothing :: Smoother     = noSmoother,
           planner    :: Planner      = getplanner,
           ⏩        :: Bool         = true) where T<:Real

(4)
function TFphase(𝐱 :: Vector{Vector{T}},
                < same arguments as method (3) >
```

(1)

Construct a [TFPhase](@ref) object computing the phase of [TFAnalyticSignal](@ref) object `Z`. By default the phase is represented in $[−π, π]$.

If optional keyword argument `unwrapped` is true (false by defalut), the phase is unwrapped, that is, it holds the cumulative sum of the phase along the time dimension once this is represented in $[0, 2π]$.

Optional keyword argument `func` is a function to be applied element-wise to the data matrix of the output. By default, the `identity` (do nothing) function is applied. If `unwrapped` is true, the function is applied on the unwrapped phase.

(2)

Construct a [TFPhaseVector](@ref) object from a [TFAnalyticSignalVector](@ref) object executing method (1) for all [TFAnalyticSignal](@ref) objects in `𝐙`

(3)

Call [`TFanalyticsignal`](@ref) to obtain the time-frequency analytic signal of real signal vector `x` and construct a [TFPhase](@ref) object holding the time-frequency phase (argument) of `x`.

All arguments are used for regulating the estimation of the analytic signal, with the exception of `unwrapped`, `func`, `fsmoothing` and `fsmoothing`.

`unwrapped` has the same meaning as in method (1) and (2).

`func` is an optional function to be applied to the phase data matrix output. If `unwrapped` is true, it is applied to the unwrapped phase.

In order to estimate the analytic signal in the time-frequency domain this function calls the [`TFanalyticsignal`](@ref) constructor (method (1) therein), with both `fsmoothing` and `tsmoothing` arguments set to `noSmoother`. `fsmoothing` and `fsmoothing` are then used to smooth the phase if `unwrapped` is true.

In order to obtain phase estimations on smoothed analytic signal instead, create a [TFAnalyticSignal](@ref) object passing a [Smoother](@ref) to the [`TFanalyticsignal`](@ref) constructor and then use method (1) to obtain the phase.

For the meaning of all other arguments, which are passed to function [`TFanalyticsignal`](@ref), see the documentation therein.

(4)

Construct a [TFPhaseVector](@ref) object from a vector of real signal vectors `𝐱`, executing method (3) for all of them. In order to estimate the time-frequency analytic signal for a vector of signals, method (2) of [`TFanalyticsignal`](@ref) is called.

**See**: [`TFanalyticsignal`](@ref), [TFPhase](@ref).

**See also**: [`phase`](@ref), [`unwrapPhase`](@ref), [`polar`](@ref).

**Examples**: see the examples of [`TFanalyticsignal`](@ref).
