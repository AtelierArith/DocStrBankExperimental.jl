In many cases, one would like to define a noise process directly by a stochastic differential equation which does not have an analytical solution. Of course, this will not be distributionally-exact and how well the properties match depends on how well the differential equation is integrated, but in many cases , this can be used as a good approximation when other methods are much more difficult.

A `NoiseApproximation` is defined by a `DEIntegrator`. The constructor for a `NoiseApproximation` is:

```julia
NoiseApproximation(source1::DEIntegrator,
    source2::Union{DEIntegrator, Nothing} = nothing;
    reset = true)
```

The `DEIntegrator` should have a final time point of integration far enough away, such that it will not halt during the integration. For ease of use, you can use a final time point as `Inf`. Note that the time points do not have to match the time points of the future integration, since the interpolant of the SDE solution will be used. Thus, the limiting factor is error tolerance, and not hitting specific points.

## NoiseApproximation Example

In this example, we will show how to use the `NoiseApproximation` to build our own Geometric Brownian Motion from its stochastic differential equation definition. In normal usage, you should use the `GeometricBrownianMotionProcess` instead since that is more efficient and distributionally-exact.

First, let's define the `SDEProblem`. Here, we use a timespan `(0.0,Inf)` so that the noise can be used over an indefinite integral.

```julia
const μ = 1.5
const σ = 1.2
f(u, p, t) = μ * u
g(u, p, t) = σ * u
prob = SDEProblem(f, g, 1.0, (0.0, Inf))
```

Now we build the noise process by building the integrator and sending that integrator to the `NoiseApproximation` constructor:

```julia
integrator = init(prob, SRIW1())
W = NoiseApproximation(integrator)
```

We can use this noise process like any other noise process. For example, we can now build a geometric Brownian motion whose noise process is colored noise that itself is a geometric Brownian motion:

```julia
prob = SDEProblem(f, g, 1.0, (0.0, Inf), noise = W)
```

The possibilities are endless.
