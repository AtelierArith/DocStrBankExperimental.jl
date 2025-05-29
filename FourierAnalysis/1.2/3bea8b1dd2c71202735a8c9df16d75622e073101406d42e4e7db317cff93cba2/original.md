```julia
(1)
function smooth(smoothing::Smoother,
                v::Vector{R}) where R<:RealOrComplex


(2)
function smooth(smoothing::Smoother,
                X::Matrix{R}; dims::Int=1) where R<:RealOrComplex

(2)
function smooth(smoother :: Smoother,
                S :: Union{FDobjects, FDobjectsVector})

(3)
function smooth(fsmoothing :: Smoother,
                tsmoothing :: Smoother,
                Y :: Union{TFobjects, TFobjectsVector})
```

Apply a smoothing function of type [Smoother](@ref) to

  * (1) a vector of real or complex numbers,
  * (2) a real of complex matrix along dimension `dims` (default=1),
  * (3) a [FDobjects](@ref) or all objects in a [FDobjectsVector](@ref),
  * (4) a [TFobjects](@ref) or all objects in a [TFobjectsVector](@ref).

Methods (1) and (2) are provided for low-level computations. Methods (3) and (4) are constructors; for all methods the output is always of the same type as the input.

Method (3) smooths across the frequency dimension:

  * for [Spectra](@ref) objects this amounts to smoothing the column vectors in their `.y` field,
  * for [CrossSpectra](@ref) and [Coherence](@ref) objects this amounts to smoothing adjacent matrices in their .y field.

Method (4) smooths across the frequency dimension, time dimension or both. This amounts to smoothing across the column vectors (frequency) and/or row vectors (time) in the `.y` field of the object. A smoother must be specified for the frequency dimension (`fsmoothing`) and for the time dimension (`tsmoothing`). Either one may be `noSmoother`, but if the two are different from `noSmoother`, then they must be the same. If smoothing is requested in both the frequency and time dimension, then the data is smoothed first in the time then in the frequency dimension. For [TFPhase](@ref) objects, smoothing is allowed only if the phase is unwrapped.

This function allow smoothing frequency domain and time-frequency domain objects after they have been created, however, smoothing can also be requested upon creation. For example, see the documentation of [Spectra](@ref).

!!! note "Nota Bene"
    For methods (1), (2) and (3), if `Smoother` is `noSmoother`, then the input is returned unchanged. For method (4) this is the case if both `fsmoother` and `tsmoother` are `noSmoother`.

    The data input must hold in the concerned dimension at least three elements for applying an Hann or Hamming smoother and at least five elements for applying the Blackman smoother.


## Maths

Smoothing of a series $x$ composed of $k$ elements is carried out at element $i$ such as

$x_{i}=ax_{i-2}+bx_{i-1}+cx_{i}+bx_{i+1}+ax_{i+2}$.

The coefficients are

| smoothing window |  a   |  b   |  c   |
|:----------------:|:----:|:----:|:----:|
|       Hann       |  0   | 0.25 | 0.50 |
|     Hamming      |  0   | 0.23 | 0.54 |
|     Blackman     | 0.04 | 0.25 | 0.42 |

For 3-point smoothers, the first point is smoothed as

$x_{1}=\frac{c}{b+c}x_{1} + \frac{b}{b+c}x_{2}$

and the last (the $k^{th}$) as

$x_{k}=\frac{c}{b+c}x_{k} + \frac{b}{b+c}x_{k-1}$.

For 5-point smoothers, the first point is smoothed as

$x_{1}=\frac{c}{a+b+c}x_{1} + \frac{b}{a+b+c}x_{2} + \frac{a}{a+b+c}x_{3}$,

the second as

$x_{2}=\frac{b}{a+2b+c}x_{1} + \frac{c}{a+2b+c}x_{2} + \frac{b}{a+2b+c}x_{3} + \frac{a}{a+2b+c}x_{4}$,

the second to last as

$x_{k-1}=\frac{a}{a+2b+c}x_{k-3} + \frac{b}{a+2b+c}x_{k-2} + \frac{c}{a+2b+c}x_{k-1} + \frac{b}{a+2b+c}x_{k}$

and the last as

$x_{k}=\frac{a}{a+b+c}x_{k-2} + \frac{b}{a+b+c}x_{k-1} + \frac{c}{a+b+c}x_{k}$.

**See**: [Smoother](@ref)

**Examples**:

```julia
using FourierAnalysis, Plots
sr, t, f, a = 128, 128, 10, 0.5
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# compute Amplitude Spectra
Σ=spectra(v, sr, t; func=√)
bar(Σ.y, labels="raw amplitude spectra")

#smooth spectra
Σ2=smooth(blackmanSmoother, Σ)
bar!(Σ2.y, labels="smoothed amplitude spectra")

# smooth cross-spectra (or coherence) matrices
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
S=crossSpectra(X, sr, t) # or coherence (X, sr, t)
# smooth the cross-spectra # or coherence
S2=smooth(blackmanSmoother, S)

# smooth time-frequency object
Y = TFanalyticsignal(v, sr, sr*4)
# smooth frequency
Z=smooth(blackmanSmoother, noSmoother, Y)
# plot amplitude of smoothed analytic signal
heatmap(Z, amplitude)

# smooth AS: smooth both frequency and time
E=smooth(blackmanSmoother, blackmanSmoother, Y)
# plot real part of smoothed analytic signal
heatmap(Z, real)
```
