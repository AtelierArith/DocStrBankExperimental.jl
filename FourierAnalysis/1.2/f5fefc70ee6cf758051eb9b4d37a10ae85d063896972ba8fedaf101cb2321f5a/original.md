```julia
(1)
function extract(S :: FDobjects,
            frange :: fInterval)

(2)
function extract(𝐒 :: FDobjectsVector,
            frange :: fInterval;
        w :: Vector = [],
    check :: Bool   = true)

(3)
function extract(Y :: TFobjects,
            frange :: fInterval,
            trange :: tInterval)

(4)
function extract(𝒀 :: TFobjectsVector,
            frange :: fInterval,
            trange :: tInterval;
        w :: Vector = [],
    check :: Bool   = true)
```

**alias**: `extr`

Extract data in a frequency region from [FDobjects](@ref) and data in a time-frequency region from [TFobjects](@ref). The frequency and time region are indicated by `frange` and `trange`, which are of type [fInterval](@ref) and [tInterval](@ref), respectively.

The input/output types of this function for a region with more then one frequency and more than one sample is reported in the following table:

| method | input object                   | output                                                               |
|:------:|:------------------------------ |:-------------------------------------------------------------------- |
| (1.1)  | [Spectra](@ref)                | a real matrix with spectra in `frange` arranged in columns¹          |
| (1.2)  | [CrossSpectra](@ref)           | a vector of complex matrices holding the cross-spectra in `frange`²  |
| (1.3)  | [Coherence](@ref)              | a vector of real matrices holding the coherence in `frange`²         |
| (2.1)  | [SpectraVector](@ref)          | a vector of matrices of type (1.1)                                   |
| (2.2)  | [CrossSpectraVector](@ref)     | a vector of vectors of type (1.2)                                    |
| (2.3)  | [CoherenceVector](@ref)        | a vector of vectors of type (1.3)                                    |
| (3.1)  | [TFAnalyticSignal](@ref)       | a complex matrix holding the analytic signal in [`frange`, `trange`] |
| (3.2)  | [TFAmplitude](@ref)            | a real matrix holding the amplitude in [`frange`, `trange`]          |
| (3.3)  | [TFPhase](@ref)                | a real matrices holding the phase in [`frange`, `trange`]            |
| (4.1)  | [TFAnalyticSignalVector](@ref) | a vector of matrices of type (3.1)                                   |
| (4.2)  | [TFAmplitudeVector](@ref)      | a vector of matrices of type (3.2)                                   |
| (4.3)  | [TFPhaseVector](@ref)          | a vector of matrices of type (3.3)                                   |

Legend: ¹ *each column refers to a time-series on which the spectra have been computed.* ² *depending on how the objects has been created, the matrices may be either Hermitian or LowerTriangular. See the documentation of [CrossSpectra](@ref) and [Coherence](@ref).

Note that depending on the arguments the type of the output may loose one or two dimensions. For instance,

  * if the [Spectra](@ref) object holds only one spectrum, (1.1) will output a column vector and (2.1) a vector of column vectors.
  * if `frange` points to a single frequency, (1.1) will output a row vector and (2.1) a vector of row vectors.
  * if both the above two conditions hold, (1.1) will output a real number and (2.1) a vector.
  * if `frange` points to a single frequency, (1.2), (1.3) will output a matrix and (2.2), (2.3) a vector of matrices.
  * If `frange` points to a single frequency band, (3.1), (3.2), (3.3) will output a row vector and (4.1), (4.2), (4.3) a vector of row vectors.
  * If `trange` points to a single time sample, (3.1), (3.2), (3.3) will output a column vector and (4.1), (4.2), (4.3) a vector of column vectors.
  * if both the above two conditions hold, (3.1), (3.2), (3.3) will output a number and (4.1), (4.2), (4.3) a vector.

Method (2) and (4) allows the following *optional keyword arguments*:

`w`, a $k$-vector of non-negative integers or real numbers, where $k$ is the numbers of objects hold in the input [FDobjectsVector](@ref) or [TFobjectsVector](@ref). `w` is a vector of weights for the regions extracted from the input objects. By default, no weights are assigned.

`check`, a boolean. If it is true (default), it is checked that the non-data fields of the input objects are all the same (for example, sampling rate, bandwidth, etc.). Set it to false to improve speed.

**See also**: [`mean`](@ref).

**Examples**:

```julia
using FourierAnalysis

# example with univariate Spectra objects (one series -> one spectrum)
sr, t, f, a = 128, 256, 10, 1
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# compute univariate spectra
Σ=spectra(v, sr, t)
# spectra in between 8Hz and 12Hz
s=extract(Σ, (8, 12))
# spectra in between 8Hz and 12.5Hz
s=extract(Σ, (8, 12.5))
# spectra at 10Hz
s=extract(Σ, 10) # or s=extract(S, (10, 10))
# these two expressions are equivalent: s=extract(Σ, :), s=Σ.y

# example with multivariate spectra (several series -> several spectra)
Σ=spectra(hcat(v, v+randn(t*16)), sr, t)
# spectra in between 8Hz and 12Hz
S=extract(Σ, (8, 12))
# spectra at 10Hz
S=extract(Σ, 10)

# example with CrossSpectra objects (the same goes for Coherence objects)
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# cross-spectra in between 8Hz and 12Hz (Hermitian matrices)
S=extract(Σ, (8, 12))
Σ=crossSpectra(X, sr, t; tril=true)
# cross-spectra in between 8Hz and 12Hz (LowerTriangular matrices)
S=extract(Σ, (8, 12))

# example with multiple cross-spectra
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # this is a CrossSpectraVector
S=extract(Σ, (8, 12); w=[0.4, 0.6])
# now S[1] holds the cross-spectra in range 8-12Hz for X
# and S[2] holds the cross-spectra in range 8-12Hz for X2

# example with time-frequency objects
# (work in the same way for TFAnalyticSignal, TFAmplitude and TFPhase)
Y = TFanalyticsignal(v, sr, t)
# analytic signal within frequencies 8Hz and 12Hz and time samples 1 to 64.
AS=extract(Y, (8, 12), (1, 64))

# all analytic signal within frequencies 8Hz and 12Hz.
AS=extract(Y, (8.0, 12), :) # accept integers and reals for frequencies

# all analytic signal within time samples 1 to 64.
AS=extract(Y, :, (1, 64))

# example with multiple time-frequency objects
# (notice how the type of the output changes)
Y = TFanalyticsignal([v, v+randn(t*16)], sr, t)
AS=extract(Y, (8, 12), (1, 64))
AS=extract(Y, (8), :)
AS=extract(Y, 8, 2)
```
