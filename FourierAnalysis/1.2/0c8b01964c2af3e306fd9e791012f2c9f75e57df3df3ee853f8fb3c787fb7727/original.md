Construct a [Taper](@ref) objects holding Slepian's multi-tapering *discrete prolate spheroidal sequences*, given sampling rate `sr`, window length `wl` and the `bandwidth` argument in Hz. For EEG data, 1<=bandwidth<=2 is an adequate choice.

The 'half-bandwidth' parameter `α` used in the DSP package and in the universal [Taper](@ref) constructor is set as

```
    `α=(bandwidth/2)*wl/sr`.
```

The optimal number of dpss is heuristically set to

```
    `n=max(1, trunc(Int, 2*α)-trunc(Int, log(2*α)))`.
```

The created object can be passed as argument in constructors [`spectra`](@ref), [`crossSpectra`](@ref) and [`coherence`](@ref).

**See**: [plot tapering windows](@ref).

**Examples**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 10, 0.5
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# create a data matrix
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
# compute spectra using slepian multi-tapering with bandwidth 1.5
H=slepians(sr, t, 2)
S=spectra(X, sr, t; tapering=H)

using Plots
plot(H)
plot(S)
```
