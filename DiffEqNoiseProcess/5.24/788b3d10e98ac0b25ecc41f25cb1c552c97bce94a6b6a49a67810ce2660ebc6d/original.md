A noise grid builds a noise process from arrays of points. For example, you can generate your desired noise process as an array `W` with timepoints `t`, and use the constructor:

```julia
NoiseGrid(t, W, Z = nothing; reset = true)
```

to build the associated noise process. This process comes with a linear interpolation of the given points, and thus the grid does not have to match the grid of integration. Thus, this can be used for adaptive solutions as well. However, one must take note that the fidelity of the noise process is linked to how fine the noise grid is determined: if the noise grid is sparse on points compared to the integration, then its distributional properties may be slightly perturbed by the linear interpolation. Thus, it's suggested that the grid size at least approximates the number of time steps in the integration to ensure accuracy.

For a one-dimensional process, `W` should be an `AbstractVector` of `Number`s. For mulitidimensional processes, `W` should be an `AbstractVector` of the `noise_prototype`.

## NoiseGrid

In this example, we will show you how to define your own version of Brownian motion using an array of pre-calculated points. In normal usage, you should use `WienerProcess` instead, since this will have distributionally-exact interpolations while the noise grid uses linear interpolations, but this is a nice example of the workflow.

To define a `NoiseGrid` you need to have a set of time points and a set of values for the process. Let's define a Brownian motion on `(0.0,1.0)` with a `dt=0.001`. To do this,

```julia
dt = 0.001
t = 0:dt:1
brownian_values = cumsum([0; [sqrt(dt) * randn() for i in 1:(length(t) - 1)]])
```

Now we build the `NoiseGrid` using these values:

```julia
W = NoiseGrid(t, brownian_values)
```

We can then pass `W` as the `noise` argument of an `SDEProblem` to use it in an SDE.
