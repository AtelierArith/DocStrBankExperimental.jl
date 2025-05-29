```julia
NoiseProcess{T, N, Tt, T2, T3, ZType, F, F2, inplace, S1, S2, RSWM, C, RNGType} <:
{T, N, Vector{T2}, inplace}
```

A `NoiseProcess` is a type defined as:

```julia
NoiseProcess(t0, W0, Z0, dist, bridge;
    iip = SciMLBase.isinplace(dist, 3),
    rswm = RSWM(), save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true)
```

  * `t0` is the first timepoint
  * `W0` is the first value of the process.
  * `Z0` is the first value of the pseudo-process. This is necessary for higher order algorithms. If it's not needed, set to `nothing`.
  * `dist` the distribution of the steps over time.
  * `bridge` the bridging distribution. Optional, but required for adaptivity and interpolating at new values.
  * `covariance` is the covariance matrix of the noise process. If not provided, the noise is assumed to be uncorrelated in each variable.
  * `save_everystep` whether to save every step of the Brownian timeseries.
  * `rng` the local RNG used for generating the random numbers.
  * `reset` whether to reset the process with each solve.
  * `reseed` whether to reseed the process with each solve.

The signature for the `dist` is

```julia
dist!(rand_vec, W, dt, rng)
```

for inplace functions, and

```julia
rand_vec = dist(W, dt, rng)
```

otherwise. The signature for `bridge` is

```julia
bridge!(rand_vec, W, W0, Wh, q, h, rng)
```

and the out of place syntax is

```julia
rand_vec = bridge!(W, W0, Wh, q, h, rng)
```

Here, `W` is the noise process, `W0` is the left side of the current interval, `Wh` is the right side of the current interval, `h` is the interval length, and `q` is the proportion from the left where the interpolation is occurring.

## Direct Construction Example

The easiest way to show how to directly construct a `NoiseProcess` is by example. Here we will show how to directly construct a `NoiseProcess` which generates Gaussian white noise.

This is the noise process, that uses `randn!`. A special dispatch is added for complex numbers for `(randn()+im*randn())/sqrt(2)`. This function is `DiffEqNoiseProcess.wiener_randn` (or with `!` respectively).

The first function that must be defined is the noise distribution. This is how to generate $W(t+dt)$ given that we know $W(x)$ for $x∈[t₀,t]$. For Gaussian white noise, we know that

$$
W(dt) ∼ N(0,dt)
$$

for $W(0)=0$ which defines the stepping distribution. Thus, its noise distribution function is:

```julia
@inline function WHITE_NOISE_DIST(W, dt, rng)
    if W.dW isa AbstractArray && !(W.dW isa SArray)
        return @fastmath sqrt(abs(dt)) * wiener_randn(rng, W.dW)
    else
        return @fastmath sqrt(abs(dt)) * wiener_randn(rng, typeof(W.dW))
    end
end
```

for the out of place versions, and for the inplace versions

```julia
function INPLACE_WHITE_NOISE_DIST(rand_vec, W, dt, rng)
    wiener_randn!(rng, rand_vec)
    sqrtabsdt = @fastmath sqrt(abs(dt))
    @. rand_vec *= sqrtabsdt
end
```

Optionally, we can provide a bridging distribution. This is the distribution of $W(qh)$ for $q∈[0,1]$ given that we know $W(0)=0$ and $W(h)=Wₕ$. For Brownian motion, this is known as the Brownian Bridge, and is well known to have the distribution:

$$
W(qh) ∼ N(qWₕ,(1-q)qh)
$$

Thus, we have the out-of-place and in-place versions as:

```julia
function WHITE_NOISE_BRIDGE(W, W0, Wh, q, h, rng)
    if W.dW isa AbstractArray
        return @fastmath sqrt((1 - q) * q * abs(h)) * wiener_randn(rng, W.dW) + q * Wh
    else
        return @fastmath sqrt((1 - q) * q * abs(h)) * wiener_randn(rng, typeof(W.dW)) +
                         q * Wh
    end
end
function INPLACE_WHITE_NOISE_BRIDGE(rand_vec, W, W0, Wh, q, h, rng)
    wiener_randn!(rng, rand_vec)
    #rand_vec .= sqrt((1.-q).*q.*abs(h)).*rand_vec.+q.*Wh
    sqrtcoeff = @fastmath sqrt((1 - q) * q * abs(h))
    @. rand_vec = sqrtcoeff * rand_vec + q * Wh
end
```

These functions are then placed in a noise process:

```julia
NoiseProcess(t0, W0, Z0, WHITE_NOISE_DIST, WHITE_NOISE_BRIDGE; kwargs)
NoiseProcess(t0, W0, Z0, INPLACE_WHITE_NOISE_DIST, INPLACE_WHITE_NOISE_BRIDGE; kwargs)
```

Notice that we can optionally provide an alternative adaptive algorithm for the timestepping rejections. `RSWM()` defaults to the Rejection Sampling with Memory 3 algorithm (RSwM3).

Note that the standard constructors are simply:

```julia
function WienerProcess(t0, W0, Z0 = nothing)
    NoiseProcess(t0, W0, Z0, WHITE_NOISE_DIST, WHITE_NOISE_BRIDGE; kwargs)
end
function WienerProcess!(t0, W0, Z0 = nothing)
    NoiseProcess(t0, W0, Z0, INPLACE_WHITE_NOISE_DIST, INPLACE_WHITE_NOISE_BRIDGE; kwargs)
end
```

These will generate a Wiener process, which can be stepped with `step!(W,dt)`, and interpolated as `W(t)`.
