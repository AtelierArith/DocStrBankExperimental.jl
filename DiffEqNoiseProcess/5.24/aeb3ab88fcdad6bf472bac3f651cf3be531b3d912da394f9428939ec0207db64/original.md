A `VirtualBrownianTree` builds the noise process starting from an initial time `t0`, the first value of the process `W0`, and (optionally) the first value `Z0` for an auxiliary pseudo-process. The constructor is given as

```julia
VirtualBrownianTree(t0,
    W0,
    Z0 = nothing,
    dist = WHITE_NOISE_DIST,
    bridge = VBT_BRIDGE;
    kwargs...)
```

where `dist` specifies the distribution that is used to generate the end point(s) `Wend` (`Zend`) of the noise process for the final time `tend`. `bridge` denotes the distribution of the employed Brownian bridge.  Per default `tend` is fixed to `t0+1` but can be changed by passing a custom `tend` as a keyword argument. The following keyword arguments are available:

  * `tend` is the end time of the noise process.
  * `Wend` is the end value of the noise process.
  * `Zend` is the end value of the pseudo-noise process.
  * `atol` represents the absolute tolerance determining when the recursion is terminated.
  * `tree_depth` allows one to store a cache of seeds, noise values, and times to speed up the simulation by reducing the recursion steps.
  * `search_depth` maximal search depth for the tree if `atol` is not reached.
  * `rng` the splittable PRNG used for generating the random numbers. Default: `Threefry4x()` from the Random123 package.

## VirtualBrownianTree Example

In this example, we define a mulitidimensional Brownian process based on a `VirtualBrownianTree` with a minimal `tree_depth=0` such that memory consumption is minimized.

```julia
W0 = zeros(10)
W = VirtualBrownianTree(0.0, W0; tree_depth = 0)

prob = NoiseProblem(W, (0.0, 1.0))
sol = solve(prob; dt = 1 / 10)
```

Using a look-up cache by increasing `tree_depth` can significantly reduce the runtime. Thus, the `VirtualBrownianTree` allows for trading off speed for memory in a simple manner.
