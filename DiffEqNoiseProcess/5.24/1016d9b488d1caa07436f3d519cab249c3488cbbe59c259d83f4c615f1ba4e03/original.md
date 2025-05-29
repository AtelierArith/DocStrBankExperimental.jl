```julia
NoiseTransport{T, N, wType, zType, Tt, T2, T3, TRV, Trv, RNGType, inplace} <:
AbstractNoiseProcess{T, N, nothing, inplace}
```

This allows you to define stochastic processes of the form `W(t) = f(u, p, t, RV)`, where `f` is a function and `RV` represents a random variable. This will use the function lazily, only caching values required to minimize function calls, but not storing the entire noise array. This requires an initial time point `t0` in the domain of `W`. A second function is needed if the desired SDE algorithm requires multiple processes.

```julia
NoiseTransport{iip}(t0,
    W,
    RV,
    rv,
    Z = nothing;
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true,
    reseed = true,
    noise_prototype = W(nothing, nothing, t0, rv)) where {iip}
```

```julia
NoiseTransport(t0,
    W,
    RV;
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true,
    reseed = true,
    kwargs...)
```

Additionally, one can use an in-place function `W(out, u, p, t, rv)` for more efficient generation of the arrays for mulitidimensional processes. When the in-place version is used without a dispatch for the out-of-place version, the `noise_prototype` needs to be set.

## NoiseTransport Example

The `NoiseTransport` requires you to pass an initial time, a transport function, and a random variable. The random variable can be either out-of-place or in-place. It is assumed it is out-of-place when the realization is a subtype of `Number`, and in-place, when it is a subtype of `AbstractArray`. Here, a random variable is any function that accepts a random number generator, in the out-of-place case (e.g. `rand(rng)`), or a random number generator and a realization to be mutated (e.g. `rand!(rng, rv)`).

An optional realization `rv` may be given. The realization `rv` is used in the first time an `AbstractRODEProblem` is solved. Subsequent runs of the same problem will draw a different realization from the random variable `RV`, unless `reseed` is set to false. In the case of a `NoiseProblem`, however, a new realization will happen at the first run already, and, in this case, `rv` can be regarded as a realization prototype, which is necessary in the case of a random vector.

As a first example, let us implement the Gaussian noise `W(t) = sin(Yt)`, where `Y` is a normal random variable.

```julia
f(u, p, t, rv) = sin(rv * t)
t0 = 0.0
W = NoiseTransport(t0, f, randn)
```

If we want to build a scalar random process out of a random vector, then an in-place version of the random vector is required, as follows. We can also use parameters in the transport function, in which case the `noise_prototype` must be given.

```julia
using Random: randn!
f(u, p, t, rv) = sin(p[1] * t + rv[1]) + cos(p[2] * t + rv[2])
t0 = 0.0
rv = randn(2)
p = (π, 2π)
W = NoiseTransport(t0, f, randn!, rv, noise_prototype = f(nothing, p, t0, rv))
```

If the random process is expected to be mulitidimensional, it is preferable to use an in-place transport function, and, in this case, the `noise_prototype` must be given. Here is an example with a scalar random vector with a beta distribution, from `Distributions.jl`.

```julia
f!(out, u, p, t, rv) = (out .= sin.(rv * t))
t0 = 0.0
RV(rng) = rand(rng, Beta(2, 3))
rv = 0.0
W = NoiseTransport(t0, f!, RV, rv, noise_prototype = zeros(4))
```

We can also have a random vector with a mulitidimensional process, in which case an in-place version of `RV` is required. For example.

```julia
using Random: randn!

function f!(out, u, p, t, v)
    out[1] = sin(v[1] * t)
    out[2] = sin(t + v[2])
    out[3] = cos(t) * v[1] + sin(t) * v[2]
    nothing
end

t0 = 0.0
RV!(rng, v) = (v[1] = randn(rng); v[2] = rand(rng))
rv = zeros(2)

W = NoiseTransport(t0, f!, RV!, rv, noise_prototype = zeros(3))
```

A `NoiseTransport` can be used as driving noise for SDEs and RODEs. Have fun!
