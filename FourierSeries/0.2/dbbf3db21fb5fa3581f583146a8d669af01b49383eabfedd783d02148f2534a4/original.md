# Function call

`fourierSeriesSampledReal(t,u,T,hMax)`

# Description

Calculates the real Fourier coefficients of a sampled function `u(t)` based on the data pairs `t` and `u`

# Function arguments

`t` Vector of sample times

`u` Data vector of which Fourier coefficients shall be determined of, i.e., `u[k]` is the sampled data value associated with `t[k]`

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
ts = [ 0; 1; 2; 3; 4; 5; 6; 7; 8; 9]    # Sampled time data
us = [-1;-1;-1;-1;-1; 1; 1; 1; 1; 1]    # Step function of square wave
T = 10                      # Period
hMax = 7                    # Maximum harmonic number
(h, f, a, b) = fourierSeriesSampledReal(ts, us, hMax)
(t, u) = fourierSeriesSynthesisReal(f, a, b)
using PyPlot
# Extend (t, u) by one element to right periodically
(tx, ux) = repeatPeriodically(ts, us, right=1)
plot(tx, ux, marker="o")    # Square wave function
plot(t, u)                  # Fourier approximation up to hMax = 7
```
