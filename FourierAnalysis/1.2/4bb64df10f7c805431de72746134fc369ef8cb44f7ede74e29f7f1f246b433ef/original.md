```julia
function bands(S :: Union{FDobjects, FDobjectsVector}
       bandwidth :: IntOrReal)
```

Return band-pass average of spectral, cross-spectral or coherence estimates in equally spaced band-pass regions with the given `bandwidth`. `bandwidth` can be given as an integer or as a real number. See [`bbands`](@ref) for details on the definition of band-pass regions.

Band-pass average is not supported for time-frequency objects as for those objects a similar averaging is natively avaiable using argument `bandwidth` in their constructors.

The output of this function is as it follows:

  * for univariate [Spectra](@ref) objects (i.e., those hodling one spectrum only), a real column vector,
  * for multivariate [Spectra](@ref) objects, a real matrix,
  * for [SpectraVector](@ref) objects, a vector of the above,
  * for [CrossSpectra](@ref) and [Coherence](@ref) objects, a vector of Hermitian or LowerTriangular matrices, depending on how the object has been cosntructed,
  * for [CrossSpectraVector](@ref) and [CoherenceVector](@ref) objects, a vector  of the above.

**See**: [`bbands`](@ref).

**Examples**:

```julia
using FourierAnalysis, Plots

# example with univariate Spectra objects (one series -> one spectrum)
sr, t, f, a = 128, 256, 10, 1
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# compute the spectrum
Σ=spectra(v, sr, t)
# mean spectra in 2Hz-band-pass regions
b=bands(Σ, 2)
plot(b)

# example with multivariate spectra (several series -> several spectra)
Σ=spectra(hcat(v, v+randn(t*16), v+randn(t*16) ), sr, t)
# mean spectra in 2Hz-band-pass regions for all time-series
b=bands(Σ, 2)
plot(b)
# plot mean spectra in 2Hz-band-pass regions for time-series 2 and 3 only
plot(bands(Σ, 2)[:, 2:3])

# example with CrossSpectra objects (the same goes for Coherence objects)
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra(X, sr, t)
# mean cross-spectra in 4Hz-band-pass regions
B=bands(Σ, 4)

# example with multiple CrossSpectra objects
X2=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
Σ=crossSpectra([X, X2], sr, t) # this is a CrossSpectraVector
# mean cross-spectra in 4Hz-band-pass regions for all cross-spectra objects
B=bands(Σ, 4)
```
