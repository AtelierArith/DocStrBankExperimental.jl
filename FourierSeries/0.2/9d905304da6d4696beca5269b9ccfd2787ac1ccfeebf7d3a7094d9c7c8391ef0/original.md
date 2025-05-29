# Function call

`fourierSeriesStepReal(t, u, T, hMax)`

# Description

Calculates the real Fourier coefficients of a step function `u(t)` based on the data pairs `t` and `u` according to the following variables:

$$
\mathtt{a[k]} =
\frac{2}{\mathtt{T}} \int_{\mathtt{t[1]}}^{\mathtt{t[1]+T}}
\mathtt{u(t)} \cos(k\omega \mathtt{t}) \operatorname{d}\mathtt{t} \\
$$

$$
\mathtt{b[k]} =
\frac{2}{\mathtt{T}} \int_{\mathtt{t[1]}}^{\mathtt{t[1]+T}}
\mathtt{u(t)} \sin(k\omega \mathtt{t}) \operatorname{d}\mathtt{t}
$$

# Function arguments

`t` Time vector instances where a step occurs

`u` Data vector of which Fourier coefficients shall be determined of, i.e., `u[k]` is the data value from the right at `t[k]`

`T` Time period of `u`

`hMax` Maximum harmonic number to be determined

# Return values

`h` Vector of harmonic numbers start at, i.e., `h[1] = 0` (dc value of `u`), `h[hMax+1] = hMax`

`f` Frequency vector associated with harmonic numbers, i.e. `f = h / T`

`a` Cosine coefficients of Fourier series, where `a[1]` = dc value of `u`

`b` Sine coefficients of Fourier series, where `b[1] = 0`

# Examples

Copy and paste code:

```julia
# Fourier approximation of square wave form
ts = [0; 1]                 # Sampled time data
us = [-1; 1]                # Step function of square wave
T = 2                       # Period
hMax = 7                    # Maximum harmonic number
(h, f, a, b) = fourierSeriesStepReal(ts, us, T, hMax)
(t, u) = fourierSeriesSynthesisReal(f, a, b)
using PyPlot
# Extend (t, u) by one element to right periodically
(tx, ux) = repeatPeriodically(ts, us, right=1)
step(tx, ux, where="post")  # Square wave function
plot(t, u)                  # Fourier approximation up to hMax = 7
```
