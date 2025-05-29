```julia
(1)
function meanDirection( 𝐙         :: TFAnalyticSignalVector,
                        frange    :: fInterval,
                        trange    :: tInterval;
                    nonlinear :: Bool       = false,
                    mode      :: Function   = extract,
                    func      :: Function   = identity,
                    w         :: Vector     = [],
                    check     :: Bool       = true)

(2)
function meanDirection( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
                 nonlinear     :: Bool         = false,
                 mode          :: Function     = extract,
                 func          :: Function     = identity,
                 w             :: Vector       = [],
                 check         :: Bool         = true,
                 filtkind      :: FilterDesign = Butterworth(2),
                 fmin          :: IntOrReal    = bandwidth,
                 fmax          :: IntOrReal    = sr÷2,
                 fsmoothing    :: Smoother     = noSmoother,
                 tsmoothing    :: Smoother     = noSmoother,
                 planner       :: Planner      = getplanner,
                 ⏩           :: Bool         = true) where T<:Real
```

This function features two methods that use exactly the same syntax as the two corresponding methods of the [`concentration`](@ref) function. All arguements have exactly the same meaning as therein. Only the output differs:

if optional keyword parameter `nonlinear` is false (default), estimate the [(weighted) mean direction](@ref) measure, otherwise estimate the [(weighted) phase mean direction](@ref) measure.

**alias**: mdir

**See also**: [`meanAmplitude`](@ref), [`concentration`](@ref), [timefrequencybi.jl](@ref).

**Examples**: see the examples of [`meanAmplitude`](@ref).
