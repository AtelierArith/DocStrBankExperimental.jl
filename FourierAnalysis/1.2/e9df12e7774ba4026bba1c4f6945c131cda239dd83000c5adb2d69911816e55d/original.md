```julia
(1)
function mean(S :: FDobjects,
         frange :: fInterval)

(2)
function mean(𝐒 :: FDobjectsVector,
         frange :: fInterval;
        w :: Vector = [],
    check :: Bool   = true)

(3)
function mean(Y :: TFobjects,
         frange :: fInterval,
         trange :: tInterval)

(4)
function mean(𝒀 :: TFobjectsVector,
         frange :: fInterval,
         trange :: tInterval;
          w :: Vector = [],
      check :: Bool   = true)
```

Return the mean of data in a frequency region from [FDobjects](@ref) and data in a time-frequency region from [TFobjects](@ref). The frequency and time region are indicated by `frange` and `trange`, which are of type [fInterval](@ref) and [tInterval](@ref), respectively.

The complete input/output types for this function is reported in the following table:

| method | input object                   | output                                                                    |
|:------:|:------------------------------ |:------------------------------------------------------------------------- |
| (1.1)  | [Spectra](@ref)                | a vector holding the mean spectra in `frange`¹                            |
| (1.2)  | [CrossSpectra](@ref)           | a complex matrix holding the mean cross-spectra in `frange`²              |
| (1.3)  | [Coherence](@ref)              | a real matrix holding the mean coherence in `frange`²                     |
| (2.1)  | [SpectraVector](@ref)          | a vector of vectors of type (1.1)                                         |
| (2.2)  | [CrossSpectraVector](@ref)     | a vector of matrices of type (1.2)                                        |
| (2.3)  | [CoherenceVector](@ref)        | a vector of matrices of type (1.3)                                        |
| (3.1)  | [TFAnalyticSignal](@ref)       | a complex number holding the mean analytic signal in [`frange`, `trange`] |
| (3.2)  | [TFAmplitude](@ref)            | a real number holding the mean amplitude in [`frange`, `trange`]          |
| (3.3)  | [TFPhase](@ref)                | a real number holding the mean phase in [`frange`, `trange`]              |
| (4.1)  | [TFAnalyticSignalVector](@ref) | a vector of numbers of type (3.1)                                         |
| (4.2)  | [TFAmplitudeVector](@ref)      | a vector of numbers of type (3.2)                                         |
| (4.3)  | [TFPhaseVector](@ref)          | a vector of numbers of type (3.3)                                         |

legend: ¹*each element of the vector refers to a time-series on which the spectra have been computed.* ² *depending on how the objects has been created, the matrices may be either Hermitian or LowerTriangular.*

Method (2) and (4) allows the following *optional keyword arguments*:

`w`, a $k$-vector of non-negative integers or real numbers, where $k$ is the numbers of objects hold in the input [FDobjectsVector](@ref) or [TFobjectsVector](@ref). `w` is a vector of weights for the means extracted from the input objects. By default, no weights are assigned.

`check`, a boolean. If it is true (default), it is checked that the non-data fields of the input objects are all the same (for example, sampling rate, bandwidth, etc.).

**See also**: [`extract`](@ref).

**Examples**:

```julia
using FourierAnalysis, Plots

# example with univariate Spectra objects (one series -> one spectrum)
sr, t, f, a = 128, 256, 10, 1
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# compute the spectrum
Σ=spectra(v, sr, t)
# mean spectrum in between 8Hz and 12Hz
s=mean(Σ, (8, 12))
# mean spectrum in between 8Hz and 12.5Hz
s=mean(Σ, (8, 12.5))

# example with multivariate spectra (several series -> several spectra)
Σ=spectra(hcat(v, v+randn(t*16)), sr, t)
# mean spectra in between 8Hz and 12Hz
S=mean(Σ, (8, 12))
# mean spectra at 10Hz, i.e., the spectra at 10Hz
S=mean(Σ, 10)

# example with CrossSpectra objects (the same goes for Coherence objects)
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# mean cross-spectra in between 8Hz and 12Hz (an Hermitian matrix)
S=mean(Σ, (8, 12))
Σ=crossSpectra(X, sr, t; tril=true)
# mean cross-spectra in between 8Hz and 12Hz (a LowerTriangular matrix)
S=mean(Σ, (8.0, 12.0)) # accept integers and reals for frequencies

# example with multiple CrossSpectra objects
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # this is a CrossSpectraVector
S=mean(Σ, (8, 12); w=[0.4, 0.6])
# now S[1] will hold the mean cross-spectrum in range 8-12Hz for X
# and S[2] will hold the mean cross-spectrum in range 8-12Hz for X2

# example with time-frequency objects
# (work in the same way for TFAnalyticSignal, TFAmplitude and TFPhase)
Y = TFanalyticsignal(v, sr, t)
# mean analytic signal within frequencies 8Hz and 12Hz and time samples 1 to 64.
as=mean(Σ, (8, 12), (1, 64))
# mean analytic signal within frequencies 8Hz and 12Hz.
as=mean(Σ, (8, 12), :)
# mean analytic signal within time samples 1 to 64.
as=mean(Σ, :, (1, 64))

# example with multiple time-frequency objects
Y = TFanalyticsignal([v, v+randn(t*16)], sr, t)
AS=mean(Y, (8, 12), (1, 64))
# get the mean across TFobjects of those means
m=mean(mean(Y, (8, 12), (1, 64)))
AS=mean(Y, (8), :)
AS=mean(Y, 8, 2)
```
