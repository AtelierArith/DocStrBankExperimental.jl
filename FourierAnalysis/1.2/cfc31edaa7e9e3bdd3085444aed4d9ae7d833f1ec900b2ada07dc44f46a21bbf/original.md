```julia
(1)
function TFanalyticsignal(x         :: Vector{T},
                          sr        :: Int,
                          wl        :: Int          = 0,
                          bandwidth :: IntOrReal    = 2;
                      fmin          :: IntOrReal    = bandwidth,
                      fmax          :: IntOrReal    = sr÷2,
                      filtkind      :: FilterDesign = Butterworth(2),
                      nonlinear     :: Bool         = false,
                      fsmoothing    :: Smoother     = noSmoother,
                      tsmoothing    :: Smoother     = noSmoother,
                      planner       :: Planner      = getplanner,
                      ⏩           :: Bool         = true) where T<:Real

(2)
function TFanalyticsignal(𝐱         :: Vector{Vector{T}},
                      <same arguments as method (1)>

```

(1)

Given sampling rate `sr`, construct a [TFAnalyticSignal](@ref) object from univariate data `x`, that is, a time-frequency representation of real vector `x`.

Call three functions in series performing the three following operations:

i. pass the data throught a bank of pass-band filters calling function [`filterbank`](@ref),

ii. compute the analytic signal calling function [`analyticsignal`](@ref) (method (1) therein),

iii. If requested, smooth the analytic signal along the time and/or frequency dimension calling function [`smooth`](@ref).

The arguments passed to each of these functions are:

| filterbank  | analyticsignal |    smooth    |
|:-----------:|:--------------:|:------------:|
|     `x`     |      `wl`      | `fsmoothing` |
|    `sr`     |  `nonlinear`   | `tsmoothing` |
| `bandwidth` |   `planner`    |              |
| `filtkind`  |      `⏩`       |              |
|   `fmin`    |                |              |
|   `fmax`    |                |              |
|     `⏩`     |                |              |

Refer to the documentation of each function to learn the meaning of each argument.

By default the `wl` argument is set to `length(x)`.

If `⏩` is true (default), filtering and computation fo the analytic signal are multi-threaded across band-pass regions as long as the number of the regions is at least twice the number of threads Julia is instructed to use. See [Threads](@ref).

(2)

Given sampling rate `sr`, construct a [TFAnalyticSignalVector](@ref) object from a vector of univariate data `𝐱`, that is, from the time-frequency representations of the vectors in `𝐱`.

This method operates as method (1) with the following exceptions:

By default the `wl` argument is set to `length(x)` for each vectors in `𝐱`. If another values is given, it will be used for all of them.

If `⏩` is true (default), the method is run in multi-threaded mode across the vectors in `𝐱` as long as their number is at least twice the number of threads Julia is instructed to use, otherwise this method attempts to run each analytic signal estimation in multi-threaded mode like in method (1). See [Threads](@ref).

If a `Planner` is not explicitly passed as an argument, the FFTW plan is computed once and applied for all analytic signal estimations.

**See**: [`filterbank`](@ref), [`analyticsignal`](@ref), [`smooth`](@ref).

**Examples**:

```julia
using Plots, FourierAnalysis

# generate some data
sr, t, bandwidth=128, 512, 2
h=taper(harris4, t)
x1=sinusoidal(10, 8, sr, t, 0)
x2=sinusoidal(10, 19, sr, t, 0)
x=Vector((x1+x2).*h.y+randn(t))
y1=sinusoidal(10, 6, sr, t, 0)
y2=sinusoidal(10, 16, sr, t, 0)
y=Vector((y1+y2).*h.y+randn(t))
plot([x, y])

# TFAnalyticSignal object for x (method (1))
Y = TFanalyticsignal(x, sr, sr*4; fmax=32)

# vector of TFAnalyticSignal objects for x and y (method (2))
𝒀 = TFanalyticsignal([x, y], sr, sr*4; fmax=32)

# (for shortening comments: TF=time-frequency, AS=analytic signal)

# mean AS in a TF region (8:12Hz and samples 1:128) for the first object
m=mean(𝒀[1], (8, 12), (1, 128)) # Output a complex number

# extract the AS in a TF region (8:12Hz and samples 1:128) for the first object
E=extract(𝒀[1], (8, 12), (1, 128)) # Output a complex matrix

# mean AS in a TF region (8:12Hz and samples 1:128) for the two objects
𝐦=mean(𝒀, (8, 12), (1, 128)) # Output a vector of complex numbers
# same computation without checking homogeneity of the two objects in 𝒀 (faster)
𝐦=mean(𝒀, (8, 12), (1, 128); check=false)

# extract the AS in a TF region (8:12Hz and samples 1:128) for the two objects
𝐄=extract(𝒀, (8, 12), (8, 12)) # Output a vector of complex matrices

# plot the real part of the AS of x (see unit recipes.jl)

# gather first useful attributes for the plot
using Plots.Measures
tfArgs=(right_margin = 2mm,
        top_margin = 2mm,
        xtickfont = font(10, "Times"),
        ytickfont = font(10, "Times"))

heatmap(tfAxes(Y)..., real(Y.y);
        c=:fire, tfArgs...)

# ...the imaginary part
heatmap(tfAxes(Y)..., imag(Y.y);
        c=:bluesreds, tfArgs...)

# ...the amplitude
heatmap(tfAxes(Y)..., amplitude(Y.y);
        c=:amp, tfArgs...)

# ...the amplitude of the AS smoothed in frequency and time
heatmap(tfAxes(Y)..., amplitude(smooth(hannSmoother, hannSmoother, Y).y);
        c=:fire, tfArgs...)

# ...the phase
heatmap(tfAxes(Y)..., phase(Y.y);
        c=:bluesreds, tfArgs...)

# or generate a TFAmplitude object from the AS
A=TFamplitude(Y)
# and plot it (with different colors)
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

# generate a TFPhase object
ϴ=TFphase(Y)
# and plot it (with custom colors)
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)

# compute and plot phase in [0, 2π]
heatmap(tfAxes(Y)..., TFphase(Y; func=x->x+π).y;
        c=:amp, tfArgs...)

# compute and plot unwrapped phase
heatmap(tfAxes(Y)..., TFphase(Y; unwrapped=true).y;
        c=:amp, tfArgs...)

# smooth time-frequency AS: smooth frequency
Z=smooth(blackmanSmoother, noSmoother, Y)

# plot amplitude of smoothed analytic signal
heatmap(tfAxes(Z)..., amplitude(Z.y);
        c=:amp, tfArgs...)

# not equivalently (!), create an amplitude object and smooth it:
# in this case the amplitude is smoothed, not the AS
A=smooth(blackmanSmoother, noSmoother, TFamplitude(Y))
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

# Smoothing raw phase estimates is unappropriate
# since the phase is a discontinous function, however it makes sense
# to smooth phase if the phase is unwrapped.
heatmap(tfAxes(Y)...,
        smooth(blackmanSmoother, noSmoother, TFphase(Y; unwrapped=true)).y;
        c=:amp, tfArgs...)

# smooth AS: smooth both frequency and time
E=smooth(blackmanSmoother, blackmanSmoother, Y)

# plot amplitude of smoothed analytic signal
heatmap(tfAxes(E)..., amplitude(E.y);
        c=:fire, tfArgs...)

# plot phase of smoothed analytic signal
heatmap(tfAxes(E)..., phase(E.y);
        c=:bluesreds, tfArgs...)

# not equivalently (!), create amplitude and phase objects and smooth them
A=smooth(blackmanSmoother, blackmanSmoother, TFamplitude(Y))
heatmap(tfAxes(A)..., A.y;
        c=:fire, tfArgs...)

ϴ=smooth(blackmanSmoother, blackmanSmoother, TFphase(Y, unwrapped=true))
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)

# smooth again
ϴ=smooth(blackmanSmoother, blackmanSmoother, ϴ)
heatmap(tfAxes(ϴ)..., ϴ.y;
        c=:fire, tfArgs...)
# and again ...

# create directly smoothed AS
Y=TFanalyticsignal(x, sr, t, bandwidth;
                   fmax=32,
                   fsmoothing=hannSmoother,
                   tsmoothing=hannSmoother)

# plot amplitude of smoothed analytic signal
heatmap(tfAxes(Y)..., amplitude(Y.y);
        c=:amp, tfArgs...)

# create directly smoothed Amplitude
A=TFamplitude(x, sr, t, bandwidth;
              fmax=32,
              fsmoothing=hannSmoother,
              tsmoothing=hannSmoother)

# plot smoothed amplitude
heatmap(tfAxes(A)..., A.y;
        c=:amp, tfArgs...)

# compute a TFAnalyticSignal object with non-linear AS
Y=TFanalyticsignal(x, sr, t, bandwidth; fmax=32, nonlinear=true)

# check that it is non-linear
Y.nonlinear

# check that the amplitude is now 1.0 everywhere
norm(amplitude(Y.y)-ones(eltype(Y.y), size(Y.y))) # must be zero

# plot non-linear phase
heatmap(tfAxes(Y)..., phase(Y.y);
        c=:bkr, tfArgs...)

# get the center frequencies of TFAmplitude object A
A.flabels

# extract the amplitude in a time-frequency region
extract(A, (2, 10), (1, 256)) # output a real matrix

# extract the amplitude in a time-frequency region at only one frequency
extract(A, 10, (1, 256)) # output a row vector

# extract the amplitude at one temporal sample at one frequency
extract(A, 10, 12) # or extract(A, 10.0, 12)

# extract amplitude at one temporal sample in a frequency region
extract(A, (10, 12), 12) # or extract(A, (10.0, 12.0), 12)

# extract amplitude at one temporal sample and all frequencies
extract(A, :, 12) # output a (column) vector

# compute the mean in a time-frequency region:
mean(A, (2, 10), (1, 256)) # output a real number
# is equivalent to (but may be less efficient than)
mean(extract(A, (2, 10), (1, 256)))

# using column sign for extracting all time samples
extract(A, (2, 10), :)

# This:
extract(A, :, :)
# is equivalent to this:
A.y
# but if you don't need to extract all frequencies,
# use the extract function to control what frequencies will be extracted:
# This
extract(A, (4, 5), 10)
# is not equivalent to this
A.y[4:5, 10]
# since the `extract` function finds the correct rows corresponding
# to the sought frequencies (in Hz), while A.y[4:5, 10]
# just returns the elements [4:5, 10] in the TF amplitude object

# Although the first center frequency in A is 2Hz, its
# band-pass region is 1-3Hz, therefore the frequency range 1:10 is accepted
mean(A, (1, 10), (1, 256))
# but this result in an error (see the REPL) since 0.5 is out of range:
mean(A, (0.5, 10), (1, 256))

# using a colon sign for time range
a=mean(A, (1, 10), :)
# using an integer for time range (indicates one specific sample)
a=mean(A, (1, 10), 16)

# using a colon sign for frequency range
a=mean(A, :, (1, 16))
# using a real number for frequency range
a=mean(A, 8.5, (1, 16))

# NB: the `extract` and `mean` functions work with the same syntax
#     for objects TFAnayticSignal, TFAmplitude and TFPhase.
```
