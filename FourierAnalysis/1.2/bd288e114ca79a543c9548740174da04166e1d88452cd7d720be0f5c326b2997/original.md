```julia
(5)
function coherence(𝐙₁     :: TFAnalyticSignalVector,
                   𝐙₂     :: TFAnalyticSignalVector,
                   frange :: fInterval,
                   trange :: tInterval;
              nonlinear :: Bool     = false,
              allkinds  :: Bool     = false,
              mode      :: Function = extract,
              func      :: Function = identity,
              w         :: Vector   = [],
              check     :: Bool     = true)

(6)
function coherence(𝐱₁        :: Vector{Vector{T}},
                   𝐱₂        :: Vector{Vector{T}},
                   sr        :: Int,
                   wl        :: Int,
                   frange    :: fInterval,
                   trange    :: tInterval,
                   bandwidth :: IntOrReal = 2;
              nonlinear  :: Bool         = false,
              allkinds   :: Bool         = false,
              mode       :: Function     = extract,
              func       :: Function     = identity,
              w          :: Vector       = [],
              filtkind   :: FilterDesign = Butterworth(2),
              fmin       :: IntOrReal    = bandwidth,
              fmax       :: IntOrReal    = sr÷2,
              fsmoothing :: Smoother     = noSmoother,
              tsmoothing :: Smoother     = noSmoother,
              planner    :: Planner      = getplanner,
              ⏩        :: Bool         = true) where T<:Real

```

**alias**: coh

If optional keyword parameter `nonlinear` is false (default), estimate linear [(weighted) coherence](@ref) measure, otherwise estimate the the [(weighted) phase concentration](@ref) measure.

If optional keyword argument `allkinds` is true all five [kinds of coherence](@ref) are returned. In this case the output is a 5-tuple of `Coherence` matrices, in the order:

  * *total* coherence,
  * *real* coherence,
  * *instantaneous* coherence
  * *imaginary* coherence,
  * *lagged* coherence.

If `allkinds` is false (default) only the *total* (classical) coherence is returned as a single `Coherence` matrix.

(5) The desired measure is obtained averaging across the [TFAnalyticSignal](@ref) objects in `𝐙`. Since this method uses pre-computed analytic signal objects, their `.nonlinear` field must agree with the `nonlinear` argument passed to this function.

`frange`, `trange`, `w`, `mode` and `func` have the same meaning as in the [`meanAmplitude`](@ref) function, however keep in mind that the two possible `mode` functions, i.e., [`extract`](@ref) and [`mean`](@ref), in this function operate on complex numbers.

The checks performed in the [`meanAmplitude`](@ref) function are performed here too. In addition, if `check` is true, also check that

  * if `nonlinear` is true, all objects in `𝐙` are nonlinear;
  * if `nonlinear` is false, all objects in `𝐙` are linear.

If either check fails, print an error message and return `Nothing`.

(6) Estimate the analytic signal of all data vectors in `𝐱` calling the [`TFanalyticsignal`](@ref) constructor and then use method (5) to obtained the desired measure.

`frange`, `trange`, `mode`, `func`, `w` and `check` have the same meaning as in the [`meanAmplitude`](@ref) function. The other arguments are passed to the [`TFanalyticsignal`](@ref) constructor, to which the reader is referred for understanding their action.

**See also**: [`meanAmplitude`](@ref), [`meanDirection`](@ref), [timefrequencybi.jl](@ref).

**Examples**: see the examples of [`comodulation`](@ref) function.
