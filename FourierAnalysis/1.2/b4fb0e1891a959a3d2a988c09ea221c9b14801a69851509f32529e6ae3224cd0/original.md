```julia
(1)
function meanAmplitude( 𝐀      :: TFAmplitudeVector,
                        frange :: fInterval,
                        trange :: tInterval;
                    mode   :: Function = extract,
                    func   :: Function = identity,
                    w      :: Vector   = [],
                    check  :: Bool     = true)

(2)
function meanAmplitude( 𝐙 :: TFAnalyticSignalVector,
                    < same arguments as method (1) >

(3)
function meanAmplitude( 𝐱      :: Vector{Vector{T}},
                        sr     :: Int,
                        wl     :: Int,
                        frange :: fInterval,
                        trange :: tInterval,
                     bandwidth :: IntOrReal    = 2;
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

**alias**: mamp

(1)

Given a [TFAmplitudeVector](@ref) object, estimate the [(weighted) mean amplitude](@ref) measure across those objects. The time-frequency planes of all the objects in `𝐀` should be congruent.

**arguments**:

`frange` and `trange` define a time-frequency region on which the estimation is sought. `frange` is a [fInterval](@ref) type and delimits center frequencies of the filter bank. `trange` is a [tInterval](@ref) type and delimits time samples. To obtain the estimation in the whole time-frequency plane use the column (:) sign for both arguments.

**optional keyword arguments**

If `mode=extract` is passed (default), the measure will be computed for all points in the chosen time-frequency region. If `mode=mean` is passed, it will be computed on the mean of these points (grand-average). The [`extract`](@ref) and [`mean`](@ref) functions are [generic methods](@ref) of *FourierAnalysis*.

**Note**: with `mode=mean` the output of the function is always a real number, whereas with `mode=extract` the output may be a real number, a real row or column vector or a real matrix, depending on the shape of the chosen time-frequency region.

Passing a function with the `func` argument you can [derive your own time-frequency measures](@ref).

`w` may be a vector of non-negative real weights associated to each input object. By default the unweighted version of the measure is computed.

If `check` is true (default), check that if the column sign is passed

  * as `frange` argument, all input objects have the same number of rows (center frequencies);
  * as `trange` argument, all input objects have the same number of columns (time samples).

If either check fails, print an error message and return `Nothing`. No other range checks are performed.

(2)

Given a [TFAnalyticSignalVector](@ref) object, compute the amplitude of all objects in `𝐙` and estimate the [(weighted) mean amplitude](@ref) measure across those objects as per method (1). In addition, since using this method all [TFAnalyticSignal](@ref) in `𝐙` must be `linear`, if `check` is true (default) and this is not the case, print an error and return `Nothing`. The checks on `frange` and `trange` performed by method (1) are also performed by this method.

(3)

Estimate the amplitude of all data vectors in `𝐱` calling the [`TFamplitude`](@ref) constructor and then estimate the [(weighted) mean amplitude](@ref) measure across the constructed amplitude objects as per method (1).

`frange`, `trange`, `mode`, `func`, `w` and `check` have the same meaning as in method (1). The other arguments are passed to the [`TFamplitude`](@ref) constructor, to which the reader is referred for their meaning.

**See also**: [`concentration`](@ref), [`meanDirection`](@ref), [timefrequencybi.jl](@ref).

**Examples**:

```julia
using FourierAnalysis

# generate 100 vectors of data
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
𝐱=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]

𝐘=TFanalyticsignal(𝐱, sr, t, bandwidth; fmax=32)
𝐀=TFamplitude(𝐘)

# mean amplitude in a TF region from a TFAnalyticSignalVector object
MAmp=meanAmplitude(𝐘, (4, 16), :)
heatmap(MAmp; c=:fire) # y axis labels are not correct

# mean amplitude in a TF region from a TFAmplitudeVector object
MAmp=meanAmplitude(𝐀, (4, 16), :)

# mean amplitude in a TF region directly from data
MAmp=meanAmplitude(𝐱, sr, t, (4, 16), :, bandwidth)

# NB: in the above, the analytic signal objects must all
# be linear, since meanAmplitude is computed from amplitude
# and the amplitude of non-linear analytic signal is uniformy equal to 1.

# All these computations can be obtained averaging in a TF region, e.g.,
MAmp=meanAmplitude(𝐘, (4, 16), :; mode=mean) # output a real number

# and can be obtained on smoothed Amplitude, e.g.,
MAmp=meanAmplitude(𝐱, sr, t, (4, 16), :;
                   fsmoothing=blackmanSmoother,
                   tsmoothing=blackmanSmoother)
# or, equivalently, and using the alias `mamp`,
MAmp=mamp(smooth(blackmanSmoother, blackmanSmoother, 𝐀), (4, 16), :)

# A similar syntax is used for the other univariate measures, e.g.,
# concentration averaging in a TF region from a TFAnalyticSignalVector object
ConM=concentration(𝐘, (4, 16), (128, 384); mode=mean)

# concentration in a TF region directly from data (using the alias `con`)
ConE=con(𝐱, sr, t, (4, 16), (128, 384), bandwidth; mode=extract)
heatmap(Con; c=:fire) # y axis labels are not correct

NB: ConM is not at all equivalent to mean(ConE) !

# mean direction averaging in a TF region directly from data
MDir=meanDirection(𝐱, sr, t, (4, 16), :, bandwidth; mode=mean)

# mean direction in a TF region from a TFAnalyticSignalVector object
MDir=meanDirection(𝐘, (4, 16), :)

# and for the non-linear counterpart:
# phase concentration in a TF region directly from data
Con=concentration(𝐱, sr, t, (8, 12), :; nonlinear=true)

# phase concentration at a single TF point
Con=concentration(𝐱, sr, t, 10, 256; nonlinear=true)

# phase mean direction averaging in a TF region directly from data
# and using the alias `mdir`
MDir=mdir(𝐱, sr, t, (8, 12), :; mode=mean, nonlinear=true)

# If you try to compute a non-linear measure from a linear
# AnalyticSignal object you will get en error (see the REPL), e.g.,
Con=con(𝐘, (8, 12), (1, 512); mode=mean, nonlinear=true)

# In order to compute non-linear measures from analytic signal objects
# first we need to compute non-linear analytic signal objects:
𝐘=TFanalyticsignal(𝐱, sr, t, bandwidth; fmax=32, nonlinear=true)

# then, we can obtain for example the phase concentration
Con=con(𝐘, (8, 12), :; mode=mean, nonlinear=true)

# and the phase mean direction
MDir=meanDirection(𝐘, (8, 12), :; nonlinear=true)
```
