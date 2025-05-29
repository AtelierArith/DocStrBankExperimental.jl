```
DeltaMoment(; nboot = 500, conf_level = 0.95, Ygrid_length = 2048,
                 num_classes = nothing)
```

  * `nboot`: number of bootstrap repetitions. Defaults to `500`.
  * `conf_level`: the level used for confidence interval calculation with bootstrap. Default value of `0.95`.
  * `Ygrid_length`: number of quadrature points to consider when performing the kernel density estimation and the integration steps. Should be a power of 2 for efficient FFT in kernel density estimates. Defaults to `2048`.
  * `num_classes`: Determine how many classes to split each factor into to when generating distributions of model output conditioned on class.

## Method Details

The Delta moment-independent method relies on new estimators for density-based statistics.  It allows for the estimation of both distribution-based sensitivity measures and of sensitivity measures that look at contributions to a specific moment. One of the primary advantage of this method is the independence of computation cost from the number of parameters.

!!! note
    `DeltaMoment` only works for scalar output.


## API

```
gsa(f, method::DeltaMoment, p_range; samples, batch = false,
         rng::AbstractRNG = Random.default_rng())
gsa(X, Y, method::DeltaMoment; rng::AbstractRNG = Random.default_rng())
```

### Example

```julia
using GlobalSensitivity, Test

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

lb = -ones(3)*π
ub = ones(3)*π

m = gsa(ishi,DeltaMoment(),fill([lb[1], ub[1]], 3), samples=1000)


samples = 1000
X = QuasiMonteCarlo.sample(samples, lb, ub, QuasiMonteCarlo.SobolSample())
Y = ishi.(@view X[:, i] for i in 1:samples)

m = gsa(X, Y, DeltaMoment())
```
