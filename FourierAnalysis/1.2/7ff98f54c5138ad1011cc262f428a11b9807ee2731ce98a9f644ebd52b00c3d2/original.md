```julia
(1)
function amplitude(c::Complex;
                        func::Function=identity) = func(abs(c))

(2)
function amplitude(A::AbstractArray{T};
                        func::Function=identity) where T<:Complex

(3)
function amplitude(A::TFAnalyticSignal;
                        func::Function=identity)

(4)
function amplitude(𝐀::TFAnalyticSignalVector;
                        func::Function=identity)
```

(1)

Return the amplitude (modulus) of a complex number. This corresponds to Julia's [abs](https://docs.julialang.org/en/v1/base/math/#Base.abs) function. It is here provided for syntactic consistency with the following methods.

(2)

Return the amplitude of a complex array `Z`. Typically, `Z` holds analytic signal, in which case the output is the analytic (instantaneous) amplitude (also known as envelope). The output is a real array of the same size as `Z`.

(3)

Return a real matrix with the analytic (instantaneous) amplitude of the [TFAnalyticSignal](@ref) object `Z`. The output is of the same size as the data field `Z.y`.

(4)

As (3), but return a vector of amplitude matrices for all [TFAnalyticSignal](@ref) objects in 𝐀

~

In all methods if a function is provided by the optional keyword argument `func`, it is applied element-wise to the output. For example,

  * passing `func=x->x^2` will return the power,
  * passing `func=x->log(x^2)` will return the log-power,
  * passing `func=x->decibel(x^2)` will return the power in deciBels.

**See**: [TFAnalyticSignal](@ref).

**Examples**:

```julia
using FourierAnalysis, Plots
x=sinusoidal(10, 2, 128, t*4, 0).*sinusoidal(10, 1, 128, t*4, 0)

# amplitude and phase of a vector using analytic signal standard method
y=analyticsignal(x)
a=amplitude(y)
ϕ=phase(y, func=x->(x+π)/2π*50)
plot([x, a, ϕ]; labels=["signal", "amplitude", "phase"])

# see what happen if `x` contains energy in frequencies below sr/wl Hz
# (see documentation of `analyticSignal` function)
y=analyticsignal(x, 64)
a=amplitude(y)
ϕ=phase(y, func=x->(x+π)/2π*50)
plot([x, a, ϕ]; labels=["signal", "amplitude", "phase"])

# unwrapped phase
# the line below will do nothing as argument `unwrapdims` is 0 by default
ϕ2=unwrapPhase(phase(y))
# this will do the job
ϕ2=unwrapPhase(phase(y); unwrapdims=1)
plot([x, a, ϕ2./25]; labels=["signal", "amplitude", "unwr. phase"])

# amplitude from analytic signal of a data matrix holding multiple series
X=randn(t, 4)
Y=analyticsignal(X)
A=amplitude(Y)
plot(A[:, 1:2])

# phase
𝛷=phase(Y)
plot(𝛷[:, 1:1])

# unwrapped phase
𝛷2=unwrapPhase(𝛷; unwrapdims=1)
plot(𝛷2)

# phase represented in [-1, 1]
𝛷=phase(Y, func=x->(x+π)/2π)
plot(𝛷[:, 1:1])

# sine of the phase
𝛷=phase(Y, func=sin)
plot(𝛷[:, 1:1])

# get Amplitude and phase from analytic Signal
A, 𝛷=polar(Y)
A
𝛷
```
