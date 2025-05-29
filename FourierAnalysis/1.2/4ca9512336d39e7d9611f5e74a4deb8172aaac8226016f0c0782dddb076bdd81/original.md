```julia
(1)
function TFamplitude(Z::TFAnalyticSignal;
                func::Function=identity)

(2)
function TFamplitude(𝐙::TFAnalyticSignalVector;
                func::Function=identity)

(3)
function TFamplitude(x         :: Vector{T},
                     sr        :: Int,
                     wl        :: Int,
                     bandwidth :: IntOrReal = 2;
                func       :: Function     = identity,
                filtkind   :: FilterDesign = Butterworth(2),
                fmin       :: IntOrReal    = bandwidth,
                fmax       :: IntOrReal    = sr÷2,
                fsmoothing :: Smoother     = noSmoother,
                tsmoothing :: Smoother     = noSmoother,
                planner    :: Planner      = getplanner,
                ⏩        :: Bool         = true) where T<:Real =

(4)
function TFamplitude(𝐱 :: Vector{Vector{T}},
                < same arguments as method (3) >
```

(1)

Construct a [TFAmplitude](@ref) object computing the amplitude of [TFAnalyticSignal](@ref) object `Z`. Optional keyword argument `func` is a function to be applied element-wise to the data matrix of the output. By default, the `identity` (do nothing) function is applied.

(2)

Construct a [TFAmplitudeVector](@ref) object from a [TFAnalyticSignalVector](@ref) object executing method (1) for all [TFAnalyticSignal](@ref) objects in `𝐙`

(3)

Call [`TFanalyticsignal`](@ref) to obtain the time-frequency analytic signal of real signal vector `x` and construct a [TFAmplitude](@ref) object holding the time-frequency amplitude (the mudulus, often referred to as the *envelope*) of `x`.

All arguments are used for regulating the estimation of the analytic signal, with the exception of `func`, `fsmoothing` and `fsmoothing`:

`func` is an optional function to be applied to the amplitude data matrix output.

In order to estimate the analytic signal in the time-frequency domain this function calls the [`TFanalyticsignal`](@ref) constructor (method (1) therein), with both `fsmoothing` and `tsmoothing` arguments set to `noSmoother`. Arguments `fsmoothing` and `fsmoothing` are then used to smooth the amplitude.

In order to obtain amplitude estimations on smoothed analytic signal instead, create a [TFAnalyticSignal](@ref) object passing a [Smoother](@ref) to the [`TFanalyticsignal`](@ref) constructor and then use method (1) to obtain the amplitude. Such amplitude estimation can be further smoothed using the [`smooth`](@ref) function, as shown in the examples.

For the meaning of all other arguments, which are passed to function [`TFanalyticsignal`](@ref), see the documentation therein.

(4)

Construct a [TFAmplitudeVector](@ref) object from a vector of real signal vectors `𝐱`, executing method (3) for all of them. In order to estimate the time-frequency analytic signal for a vector of signals, method (2) of [`TFanalyticsignal`](@ref) is called.

**See**: [`TFanalyticsignal`](@ref), [TFAmplitude](@ref).

**See also**: [`amplitude`](@ref).

**Examples**: see the examples of [`TFanalyticsignal`](@ref).
