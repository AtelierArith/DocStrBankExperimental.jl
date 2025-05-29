```julia
(1)
function coherence(𝙎    :: CrossSpectra;
               allkinds :: Bool = false)

(2)
function coherence(𝓢    :: CrossSpectraVector;
               allkinds :: Bool = false,
               check    :: Bool = true)

(3)
function coherence(X  :: Matrix{T},
                   sr :: Int,
                   wl :: Int;
               tapering  :: Union{Taper, TaperKind} = harris4,
               planner   :: Planner                 = getplanner,
               slide     :: Int                     = 0,
               DC        :: Bool                    = false,
               nonlinear :: Bool                    = false,
               smoothing :: Smoother                = noSmoother,
               tril      :: Bool                    = false,
               allkinds  :: Bool                    = false,
               ⏩       :: Bool                    = true) where T<:Real

(4)
function coherence(𝐗 :: Vector{Matrix{T}},
              < same argument sr, ..., ⏩ of method (3) > where T<:Real


```

**alias**: coh

!!! note "export conflict"
    This identifier may conflict with the DSP package. Invoke it as `FourierAnalysis.coherence`.


(1)

Construct a [Coherence](@ref) object from a [CrossSpectra](@ref) object, allowing coherence estimates using the Welch method. All non-data fields are copied from the cross-spectra object, i.e., all fields but `y`, which holds the coherence matrices that are computed by this function.

If `𝙎.tril` is true, only the lower triangular part of the coherence matrices is computed and the matrices in `y` are LowerTriangular matrices, otherwise the full matrices are computed and `y` will hold Hermitian matrices (see [LinearAlgebra](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#Linear-Algebra-1)).

If optional keyword argument `allkinds` is true, all five [kinds of coherence](@ref) are returned. In this case the output is a 5-tuple of Coherence objects, in the order:

  * *total* coherence,
  * *real* coherence,
  * *instantaneous* coherence
  * *imaginary* coherence,
  * *lagged* coherence.

If `allkinds` is false (default), only the *total* (classical) coherence is returned as a single `Coherence` object.

(2)

Construct a [CoherenceVector](@ref) object from the input [CrossSpectraVector](@ref) object `𝓢`, allowing coherence estimates using the Welch method. This method calls method (1) for all objects in `𝓢`.

The `allkinds` optional keyword parameter has the same meaning as in method (1). In this method if the argument is passed as true, the output is a 5-tuple of `CoherenceVector` objects.

If optional keyword argument `check` is true (default), it is checked that all `CrossSpectra` objects in `𝓢` have the same value in the ``.sr`, `.wl`, `.DC`, `.taper`, `.nonlinear` and `.smoothing` field. If this is not the case, an error message is printed pointing to the first field that is not identical in all objects and `Nothing` is returned.

(3)

Given a multivariate time series data matrix `X` of dimension $t$ x $n$, where $t$ is the number of samples (rows) and $n$ the number of time-series (columns), sampling rate `sr` and epoch length `wl`, compute the squared coherence matrices of `X`, that is, the coherence matrices at all Fourier discrete frequencies obtained from the Welch (sliding window) average cross-spectra.

**optioal keyword arguments**:

`sr`, `wl`, `tapering`, `planner` and `slide` have the same meaning as for the [`spectra`](@ref) function.

`DC`, `nonlinear`, `smoothing`, `tril` and `⏩` have the same meaning as for the [`crossSpectra`](@ref) function, to which they apply for estimating the cross-spectra.

The `allkinds` optional keyword parameter has the same meaning as in method (1).

(4)

Construct a [CoherenceVector](@ref) object from a vector of real multivariate data matrices. Compute the coherence matrices from the cross-spectral matrices estimated using the Welch method as per method (3) for all $k$ data matrices in `𝐗`.

The $k$ matrices in `𝐗` must have the same number of columns (*i.e.*, the same number of time-series), but may have any number of (at least `wl`) rows (samples). All other arguments have the same meaning as in method (3), with the following difference:

`⏩`: if true (default), the method is run in multi-threaded mode across the $k$ data matrices if $k$ is at least twice the number of threads Julia is instructed to use, otherwise this method attempts to run each coherence estimation in multi-threaded mode across series as per method (3). See [Threads](@ref).

If a `Planner` is not explicitly passed as an argument, the FFTW plan is computed once and applied for all coherence estimations.

**note for methods (1) and (3)**:

If `tril` is false (default), the output coherence object(s) is of type `Array{Hermitian,1}`, which is the `ℍVector` type used in package [PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl). Since coherence estimates are symmetric positive definite, they can be straightaway used as argument to PosDefManifold's functions, e.g., for computing matrix moves on [geodesics](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Geodesic-equations-1), matrix [distances](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.distance), etc. and the the whole vector output to compute matrix [means](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Means-1), [spectral embedding](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.spectralEmbedding) and more.

If `tril` is true, the output is of type `Array{LowerTriangular,1}`, which is the `𝕃Vector` type used in PosDefManifold, that is, only the lower triangle of the coherencee is computed in order to save time and memory.

**note for methods (2) and (4)**:

If `tril` is false, the output is of type `Array{Array{Hermitian,1},1}`, which is the `ℍVector₂` type used in [PosDefManifold](https://github.com/Marco-Congedo/PosDefManifold.jl).

If `tril` is true, the output is of type `Array{Array{LowerTriangular,1},1}`, which is the `𝕃Vector₂` type used in PosDefManifold.

**See**: [crossspectra.jl](@ref), [Spectra](@ref), [Coherence](@ref).

**Examples**:

```julia
## common code for methods (1)-(4)

using FourierAnalysis, LinearAlgebra

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

# (1)

X=generateSomeData(sr, t) # multivariate data matrix 8192x4

# cross-spectra using default harris4 tapering window
S=crossSpectra(X, sr, wl)

# Only classical coherence
C=FourierAnalysis.coherence(S)

# All 5 kinds of coherence
Ctot, C2real, C3inst, C4imag, C5lag=FourierAnalysis.coherence(S, allkinds=true);
Ctot

# (2)

# generate 3 multivariate data matrices 8192x4
X=[generateSomeData(sr, t) for i=1:3]

# cross-spectra using default harris4 tapering window
S=crossSpectra(X, sr, wl)

# Only classical coherence
C=FourierAnalysis.coherence(S)

# All 5 kinds of coherence
Ctot, C2real, C3inst, C4imag, C5lag=FourierAnalysis.coherence(S, allkinds=true);
Ctot

# (3)

X=generateSomeData(sr, t) # multivariate data matrix 8192x4

# coherence using default harris4 tapering window
C=FourierAnalysis.coherence(X, sr, wl)

# check the coherence matrix at frequency 5Hz
C.y[f2b(5, sr, wl)]

# coherence using hann tapering window
C=FourierAnalysis.coherence(X, sr, wl; tapering=hann)

# using Slepian's multi-tapering
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl))

# compute non-linear coherence (phase-locking value)
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# compute only the lower triangle of coherence matrices
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# compute all five kinds of coherence
Ctot, Creal, Cinst, Cimag, Clag=FourierAnalysis.coherence(X, sr, wl;
    tapering=slepians(sr, wl), tril=true, allkinds=true);
Ctot

# smooth a-posteriori the coherence
C2=smooth(blackmanSmoother, C)

# or compute coherence already smoothed
C=FourierAnalysis.coherence(X, sr, wl;
            tapering=slepians(sr, wl), tril=true, smoothing=blackmanSmoother)

# mean coherence matrix in 8Hz-12Hz range
M=mean(C, (8, 12)) # or also M=mean(C, (8.0, 12.0))

# extract all coherence matrices in 8Hz-12Hz range
E=extract(C, (8, 12))

# coherence matrices averaged in 2Hz band-pass regions
B=bands(C, 2)

# (4)

# generate 3 multivariate data matrices 8192x4
X=[generateSomeData(sr, t) for i=1:3]

# The examples here below use exactly the same syntax as method (3).
# However, since the input here is a vector of data matrices
# and not a single data matrix, the examples here below create a vector
# of the object created by the examples of method (3).
# For example:

# coherence using the default harris4 tapering window
# this creates a CoherenceVector object
C=FourierAnalysis.coherence(X, sr, wl)

# check the first Coherence object
C[1]

# check the coherence matrix at fr. 5Hz for the first Coherence object
C[1].y[f2b(5, sr, wl)]

# coherence using Hann tapering window
C=FourierAnalysis.coherence(X, sr, wl; tapering=hann)

# using Slepian's multi-tapering
C=coherence(X, sr, wl; tapering=slepians(sr, wl))

# compute non-linear coherence
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), nonlinear=true)

# compute only the lower triangle of coherence matrices
C=FourierAnalysis.coherence(X, sr, wl; tapering=slepians(sr, wl), tril=true)

# compute all five kinds of coherence
Ctot, Creal, Cinst, Cimag, Clag=FourierAnalysis.coherence(X, sr, wl;
    tapering=slepians(sr, wl), tril=true, allkinds=true);
Ctot

# smooth a-posteriori all coherence objects in S
C2=smooth(blackmanSmoother, C)

# or compute them all already smoothed
C=FourierAnalysis.coherence(X, sr, wl; tapering=parzen, smoothing=blackmanSmoother)

# mean coherence matrix in 8Hz-12Hz range for all coherence objects
M=mean(C, (8, 12)) # or also M=mean(C, (8.0, 12.0))

# grand-average mean of the above across all Coherence objects
meanM=mean(mean(C, (8, 12)))

# extract all coherence matrices in 8Hz-12Hz range for all coherence objects
E=extract(C, (8, 12))

# grand average of coherence matrices in 8Hz-12Hz range for all coh. objects
meanE=mean(extract(C, (8, 12)))

# coherence matrices averaged in 2Hz band-pass regions for all coh. objects
B=bands(C, 2)

# Pre-compute a FFT planner and pass it as argument
# (this interesting if the function is to be called repeatedly).
plan=Planner(plan_exhaustive, 10.0, wl, eltype(X[1])) # wait 10s
C=FourierAnalysis.coherence(X, sr, wl; planner=plan)

# how faster is this?
using BenchmarkTools
@benchmark(FourierAnalysis.coherence(X, sr, wl))
@benchmark(FourierAnalysis.coherence(X, sr, wl; planner=plan))
...
...
```
