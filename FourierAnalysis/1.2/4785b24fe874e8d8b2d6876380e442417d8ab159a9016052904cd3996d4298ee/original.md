```julia
function sinusoidal(a :: IntOrReal,
                    f :: IntOrReal,
                   sr :: Int,
                    t :: Int,
                    θ :: IntOrReal = 0.;
                DClevel = 0.)
```

Generate a sinusoidal wave with peak amplitude `a`, frequency `f`, sampling rate `sr`, duration (in samples) `t`, angle `θ` (θ=0 makes a sine, θ=π/2 makes a cosine) and optional keyword argument `DC` (float), the DC level defaulting to zero. It is adopted the convention that a sine wave starts at zero.

**Examples**:

```julia
using FourierAnalysis, Plots

# create and plot a sinusoidal wave of 128 samples with
# peak amplitude 1, frequency 12Hz, sr=64, phase=π/2
v=sinusoidal(1., 12, 64, 128, π/2)
plot(v)

# estimate amplitude of a sinusoidal wave using Goertzel algorithm
f, sr, t = 32, 128, 128
v=sinusoidal(3., f, sr, t, 0)
c=goertzel(v, f, sr, t) # c should be equal to 0+3.0im
```
