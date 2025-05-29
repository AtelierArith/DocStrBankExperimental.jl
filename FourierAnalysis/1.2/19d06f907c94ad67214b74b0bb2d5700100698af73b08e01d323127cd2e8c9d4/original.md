```julia
(1)
function comodulation( 𝐀₁     :: TFAmplitudeVector,
                       𝐀₂     :: TFAmplitudeVector,
                       frange :: fInterval,
                       trange :: tInterval;
                  mode  :: Function = extract,
                  func  :: Function = identity,
                  w     :: Vector = [],
                  check :: Bool   = true) =

(2)
function comodulation( 𝐙₁     :: TFAnalyticSignalVector,
                       𝐙₂     :: TFAnalyticSignalVector,
    < arguments frange, trange, mode, func, w and check as in method (1) >

(3)
function comodulation(𝐱₁        :: Vector{Vector{T}},
                      𝐱₂        :: Vector{Vector{T}},
                      sr        :: Int,
                      wl        :: Int,
                      frange    :: fInterval,
                      trange    :: tInterval,
                      bandwidth :: IntOrReal    = 2;
                mode            :: Function     = extract,
                func            :: Function     = identity,
                w               :: Vector       = [],
                filtkind        :: FilterDesign = Butterworth(2),
                fmin            :: IntOrReal    = bandwidth,
                fmax            :: IntOrReal    = sr÷2,
                fsmoothing      :: Smoother     = noSmoother,
                tsmoothing      :: Smoother     = noSmoother,
                planner         :: Planner      = getplanner,
                ⏩             :: Bool         = true) where T<:Real

```

**alias**: com

(1)

Given a pair of [TFAmplitudeVector](@ref) objects, estimate their [(weighted) comodulation](@ref) measure. `𝐀₁` and `𝐀₂` must hold the same number of objects and the time-frequency planes of all the objects should be congruent.

**arguments**:

`frange` and `trange` have the same meaning as in the [`meanAmplitude`](@ref) method.

**optional keyword arguments**

`mode`, `func` and `check` have the same meaning as in the [`meanAmplitude`](@ref) method.

`w` may be a vector of non-negative real weights associated to each pair of input objects. By default the unweighted version of the measure is computed.

(2)

Given a pair of [TFAnalyticSignalVector](@ref) object, compute the amplitude of all objects and estimate the [(weighted) comodulation](@ref) as per method (1). Like in method (1), `𝐙₁` and `𝐙₂` must hold the same number of objects and the time-frequency planes of all the objects should be congruent. In addition, since using this method all [TFAnalyticSignal](@ref) objects in `𝐙₁` and `𝐙₂` must be `linear`, if `check` is true (default) and this is not the case, print an error and return `Nothing`. The checks on `frange` and `trange` performed by method (1) are also performed by this method.

(3)

Estimate the amplitude of all data vectors in `𝐱₁` and `𝐱₂` calling the [`TFamplitude`](@ref) constructor and then estimate the [(weighted) comodulation](@ref) measure across the constructed amplitude objects as per method (1).

`frange`, `trange`, `mode`, `func`, `w` and `check` have the same meaning as in method (1). The other arguments are passed to the [`TFamplitude`](@ref) constructors, to which the reader is referred for their meaning.

If a `planner` for FFT computations is not provided, it is computed once and applied for all amplitude estimations.

**See also**: [`coherence`](@ref), [timefrequencybi.jl](@ref).

**Examples**:

```julia
using FourierAnalysis

# generate 100 pairs of data vectors
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
𝐱₁=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]
𝐱₂=[sinusoidal(2, 10, sr, t, 0).*h.y+randn(t) for i=1:100]

# compute their (linear) analytic signal
𝐘₁=TFanalyticsignal(𝐱₁, sr, wl, bandwidth; fmax=32, nonlinear=false)
𝐘₂=TFanalyticsignal(𝐱₂, sr, wl, bandwidth; fmax=32, nonlinear=false)

# compute their amplitude
𝐀₁=TFamplitude(𝐘₁)
𝐀₂=TFamplitude(𝐘₂)

# compute the Com averaging in a TF region from TFAnalyticSignal objects
# 𝐘₁ and 𝐘₂ must be linear
Com=comodulation(𝐘₁, 𝐘₂, (8, 12), :; mode=mean)

# compute the Com averaging in a TF region from TFAmplitudeVector objects
# 𝐀₁ and 𝐀₂ must be linear
Com=comodulation(𝐀₁, 𝐀₂, (8, 12), :; mode=mean)

# compute the Com averaging in a TF region directly from data
# In this case you don't have to worry about linearity
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean)

# compute comodulation from smoothed amplitude:
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth;
                 mode=mean,
                 fsmoothing=blackmanSmoother,
                 tsmoothing=blackmanSmoother)

# you can go faster pre-computing a FFTW plan.
# This is useful when you have to call the comodulation function several times
plan=Planner(plan_patient, 5, wl, Float64, true)
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean, planner=plan)

# compute the Com in a TF region from TFAnalyticSignalVector objects
Com=comodulation(𝐘₁, 𝐘₂, (8, 12), :; mode=extract)

# compute the Com in a TF region from TFAmplitudeVector objects
Com=comodulation(𝐀₁, 𝐀₂, (8, 12), :; mode=extract)

# compute the Com in a TF region directly from data
Com=comodulation(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=extract)

# All these operations can be done also for coherence measures, for example
Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=mean)

Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=extract)

# Compute all 5 coherence types
Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=extract, allkinds=true)

# phase coherence (phase-locking value)
# we obtain this measure from non-linear TFAnalyticSignalVector objects
𝐘₁=TFanalyticsignal(𝐱₁, sr, wl, bandwidth; fmax=32, nonlinear=true)
𝐘₂=TFanalyticsignal(𝐱₂, sr, wl, bandwidth; fmax=32, nonlinear=true)

Coh=coherence(𝐘₁, 𝐘₂, (8, 12), :; mode=mean, nonlinear=true)

# or directly from data (no need to worry about non-linearity in this case)
Coh=coherence(𝐱₁, 𝐱₂, sr, wl, (8, 12), :, bandwidth; mode=mean, nonlinear=true)

```
