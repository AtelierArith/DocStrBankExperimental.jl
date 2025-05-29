```julia
(1)
function spectra( X     :: Union{Vector{T}, Matrix{T}},
                  sr    :: Int,
                  wl    :: Int;
            tapering  :: Union{Taper, TaperKind} = harris4,
            planner   :: Planner                 = getplanner,
            slide     :: Int                     = 0,
            DC        :: Bool                    = false,
            func      :: Function                = identity, # equal to x->x
            smoothing :: Smoother                = noSmoother,
            ⏩       :: Bool                    = true) where T<:Real

(2)
function spectra( 𝐗   :: Vector{Matrix{T}},
            < same argument sr, ..., ⏩ of method (1) > where T<:Real
```

(1)

Construct a [Spectra](@ref) object from real univariate or multivariate data. Given sampling rate `sr` and epoch length `wl`, compute the Welch power spectra of a vector (univariate) or of a data matrix (multivariate) `X` of dimension $t$x$n$, where $t$ is the number of samples (rows) and $n$ is the number of time-series (columns).

The spectra are hold in the `.y` field of the created object. If `X` is a vector, `.y` is a vector, whereas if `X` is a matrix, `.y` is a matrix holding in its columns the spectra of the signals in the columns of `X`. The size of the spectra depends on the `DC` optional keyword argument (see below), as reported in the documentation of the [Spectra](@ref) structure.

**Optional Keyword Arguments**:

`tapering`: this is a tapering object of type [Taper](@ref) or a tapering window kind of type [TaperKind](@ref). By default the *harris4* tapering window is used. If no tapering is sought, pass as argument `tapering=rectangular`. This same syntax is the most convenient way to specify all simple tapering window, e.g., `tapering=hann`, `tapering=hamming`, etc. For *discrete prolate spheroidal sequences (dpss)* multi-tapering, use instead the [`slepians`](@ref) constructor, e.g., pass as argument something like `tapering=slepians(sr, wl, 2)`.

`planner`: this is an instance of the [`Planner`](@ref) object, holding the forward FFTW plan used to compute the FFTs. By default the planner is computed by this method, but it can be passed as an argumet here if it is pre-computed. This is interesting if this function is to be invoked repeatedly.

`slide`: this is the number of samples the windows slide on (Welch method). By default the number of samples is chosen to allow 50% overlap.

`DC`: if true, the spectrum/a of the DC level is returned in the first row of `y` (see the fields of the [Spectra](@ref) object), otherwise (default) the rows in `y` start with the first positive discrete frequency, that is, $sr/wl$ Hz.

`func`: this is a function that operate element-wise to transfrom the power spectra before returning them, including anonymous functions. Common choices are:

  * `func=sqrt` return the amplitude spectra,
  * `func=log` return the log-power spectra,
  * `func=decibel` return the power spectra in deciBels (see [`decibel`](@ref)),

By default no function is applied and the power spectra are returned. If smoothing has been requested (see below), it is applied after the function.

`smoothing`: it applies a smoothing function of type [Smoother](@ref) to the spectra across adjacent frequencies. By default no smoothing is applied.

`⏩`: if true (default), the method run in multi-threaded mode across the series in `X` if the number of series is at least twice the number of threads Julia is instructed to use. See [Threads](@ref).

(2)

Construct a [SpectraVector](@ref) object from a vector of real univariate (vectors) or multivariate data (matrices). Compute the spectra as per method (1) for all $k$ data vectors or data matrices in `𝐗`.

If `𝐗` holds data matrices, the $k$ matrices in `𝐗` must have the same number of columns (i.e., the same number of time series), but may have any number of (at least `wl`) rows (samples). All other arguments have the same meaning as in method (1), with the following differences:

  * `⏩`: if true (default), the method run in multi-threaded mode across the   $k$ data matrices if $k$ is at least twice the number of threads Julia   is instructed to use, otherwise this method attempts to run each spectra   estimation in multi-threaded mode across series as per method (1).   See [Threads](@ref).
  * If a `planner` is not explicitly passed as an argument,   the FFTW plan is computed once and applied for all spectral estimations.

**See**: [Spectra](@ref), [plot spectra](@ref).

**See also**: [`crossSpectra`](@ref), [`coherence`](@ref), [goertzel.jl](@ref).

**Examples**:

```julia
using FourierAnalysis

###################################################################

# (1)

# Check that correct amplitude spectra is returned at all discrete
# Fourier Frequency (using a rectangular taper).
# Sinusoids are created at all frequencies with amplitude 10 at the
# first frequency and then incrementing by 10 units along frequencies.
# NB when t is even, correct amplitude for the last frequency is obtained
# only if the sinusoidal has a particular phase.

sr, t, wl= 16, 32, 16
V=Matrix{Float64}(undef, t, wl)
for i=1:wl V[:, i]=sinusoidal(10*i, b2f(i, sr, t), sr, t, π/6) end

# using FFTW.jl only
using FFTW
P=plan_rfft(V, 1)*(2/t);
Σ=abs.(P*V)
using Plots
bar(Σ[brange(t, DC=true), :], labels="")

# using FourierAnalysis.jl
Σ2=spectra(V, sr, t; tapering=rectangular, func=√, DC=true)
using Plots
bar(Σ2.y[brange(t, DC=true), :], labels="")

#############################################################################

### Check amplitude spectra on long signals obtained by welch methods
# one sinusoidal is at an exact discrete Fourier Frequency and the other not
# Rectangular window
sr, t, f, a = 128, 128, 10, 0.5
v=sinusoidal(a, f, sr, t*16)+sinusoidal(a, f*3.5+0.5, sr, t*16)+randn(t*16);
Σ=spectra(v, sr, t; tapering=rectangular, func=√)
bar(Σ.y, labels="rectangular")

# harris4 window (default)
Σ2=spectra(v, sr, t; func=√)
bar!(Σ2.y, labels="harris4")

#smooth spectra
Σ3=smooth(blackmanSmoother, Σ2)
bar!(Σ3.y, labels="smoothed")

#############################################################################

function generateSomeData(sr::Int, t::Int; noise::Real=1.)
    # four sinusoids of length t samples and sr sampling rate
    # peak amplitude: 0.7, 0.6, 0.5, 0.4
    # frequency:        5,   7,  13,  27
    # phase:            0, π/4, π/2,   π
    v1=sinusoidal(0.7, 5,  sr, t, 0)
    v2=sinusoidal(0.6, 7,  sr, t, π/4)
    v3=sinusoidal(0.5, 13, sr, t, π/2)
    v4=sinusoidal(0.4, 27, sr, t, π)
    return hcat(v1, v2, v3, v4) + (randn(t, 4)*noise)
end

sr, wl, t = 128, 512, 8192
X=generateSomeData(sr, t)
# multivariate data matrix 8192x4

# compute spectra
S=spectra(X, sr, wl)

# check the spectrum of first series
S.y[:, 1]

# gather some plot attributes to get nice plots
using Plots.Measures
spectraArgs=(fmax = 32,
             left_margin = 2mm,
             bottom_margin = 2mm,
             xtickfont = font(11, "Times"),
             ytickfont = font(11, "Times"))
plot(S; spectraArgs...)
plot(S; xspace=2, spectraArgs...)

# use a custom simple taperig window
S=spectra(X, sr, wl; tapering=riesz)

# use Slepian's multi-tapering
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5))

# construct with smoothing
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5), smoothing=hannSmoother)

# compute Amplitude Spectra instead
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.5), func=√)

# plot Aplitude spectra
plot(S; ytitle="Amplitude", spectraArgs...)

# smooth the spectra a-posteriori
S=smooth(blackmanSmoother, S)

# extract spectra in range (8Hz to 12Hz)
e=extract(S, (8, 12))

# extract spectra in range (8Hz to 12Hz) for series 1 and 2
e=extract(S, (8, 12))[:, 1:2]

# extract the spectra at 10Hz only (1 bin per series)
e=extract(S, 10)

# average spectra in the 8Hz-12Hz range
bar(mean(S, (8.0, 12.0)))

# average across series of the average spectra in the 8Hz-12Hz range
mean(mean(S, (8.0, 12.0)))

# average spectrum across all frequencies for each series
bar(mean(S, :))

# average spectra in equally-spaced 2Hz-band-pass regions for all series
plot(bands(S, 2))

# average spectra in equally-spaced 2Hz-band-pass regions for series 1 and 2
plot(bands(S, 2)[:, 1:2])

# (2)

# generate 3 multivariate data matrices 8192x4
X=[generateSomeData(sr, t) for i=1:3]

# Now the call to the spectra function will generate 3 Spectra objects
S=spectra(X, sr, wl)
plot(S[1]; spectraArgs...)
plot(S[2]; spectraArgs...)
plot(S[3]; spectraArgs...)

# when you want to compute the spectra of many data matrices you may want
# to do it using a fast FFTW plan (wait up to 10s for computing the plan)
plan=Planner(plan_exhaustive, 10.0, wl)
S=spectra(X, sr, wl; planner=plan)

# how faster is this?
using BenchmarkTools
@benchmark(spectra(X, sr, wl))
@benchmark(spectra(X, sr, wl; planner=plan))


# average spectra in range (8Hz-12Hz) for all series of all objects
M=mean(S, (8, 12))

# plot the average spectrum across all series for the three objects
# using Julia standard mean function
plot(mean(S[1].y[:, i] for i=1:size(S[1].y, 2)))
plot!(mean(S[2].y[:, i] for i=1:size(S[2].y, 2)))
plot!(mean(S[3].y[:, i] for i=1:size(S[3].y, 2)))

# average spectra in range (4Hz-32.5Hz) across objects for the 4 series
plot(mean(mean(S, (4, 32.5))))

# extract spectra in range (8Hz-12Hz) for all series and all subjects
extract(S, (8, 12))

# if you enter en illegal range, nothing will be done and you will get
# an error in the REPL explaining what is wrong in your argument
extract(S, (0, 12))
mean(S, (1, 128))

# extract 4Hz-band-pass average spectra for all series and all objects
bands(S, 4)

# Apply smoothing in the spectra computations
S=spectra(X, sr, t; smoothing=blackmanSmoother)
plot(S[1]; spectraArgs...)
plot(S[2]; spectraArgs...)
plot(S[3]; spectraArgs...)

# plot spectra in in 1Hz band-pass regions for all series in S[1]
plot(bands(S[1], 1))

# use slepian multi-tapering
S=spectra(X, sr, wl; tapering=slepians(sr, wl, 1.))
plot(S[1]; spectraArgs...)

# average spectra across objects
plot(mean(s.y for s ∈ S))


```
