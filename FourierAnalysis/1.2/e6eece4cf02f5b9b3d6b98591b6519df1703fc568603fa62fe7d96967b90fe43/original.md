```julia
(1)
function concentration( 𝐙       :: TFAnalyticSignalVector,
                        frange  :: fInterval,
                        trange  :: tInterval;
                    nonlinear :: Bool     = false,
                    mode      :: Function = extract,
                    func      :: Function = identity,
                    w         :: Vector   = [],
                    check     :: Bool     = true)

(2)
function concentration( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
                 nonlinear  :: Bool         = false,
                 mode       :: Function     = extract,
                 func       :: Function     = identity,
                 w          :: Vector       = [],
                 check         :: Bool      = true,
                 filtkind   :: FilterDesign = Butterworth(2),
                 fmin       :: IntOrReal    = bandwidth,
                 fmax       :: IntOrReal    = sr÷2,
                 fsmoothing :: Smoother     = noSmoother,
                 tsmoothing :: Smoother     = noSmoother,
                 planner    :: Planner      = getplanner,
                 ⏩        :: Bool         = true) where T<:Real

```

**alias**: con

If optional keyword parameter `nonlinear` is false (default), estimate the [(weighted) concentration](@ref) measure, otherwise estimate the [(weighted) phase concentration](@ref) measure.

(1) The desired measure is obtained averaging across the [TFAnalyticSignal](@ref) objects in `𝐙`. Since this method uses pre-computed analytic signal objects, their `.nonlinear` field must agree with the `nonlinear` argument passed to this function.

`frange`, `trange`, `w`, `mode` and `func` have the same meaning as in the [`meanAmplitude`](@ref) function, however keep in mind that the two possible `mode` functions, i.e., [`extract`](@ref) and [`mean`](@ref), in this function operate on complex numbers.

The checks performed in the [`meanAmplitude`](@ref) function are performed here too. In addition, if `check` is true, also check that

  * if `nonlinear` is true, all objects in `𝐙` are nonlinear;
  * if `nonlinear` is false, all objects in `𝐙` are linear.

If either check fails, print an error message and return `Nothing`.

(2) Estimate the analytic signal of all data vectors in `𝐱` calling the [`TFanalyticsignal`](@ref) constructor and then use method (1) to obtained the desired measure.

`frange`, `trange`, `mode`, `func`, `w` and `check` have the same meaning as in the [`meanAmplitude`](@ref) function. The other arguments are passed to the [`TFanalyticsignal`](@ref) constructor, to which the reader is referred for understanding their action.

**See also**: [`meanAmplitude`](@ref), [`meanDirection`](@ref), [timefrequencybi.jl](@ref).

**Examples**: see the examples of [`meanAmplitude`](@ref) function.
