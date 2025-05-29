```
DGSM(; crossed::Bool = false)
```

  * `crossed`: A Boolean which act as indicator for computation of DGSM crossed indices.

## Method Details

The DGSM method takes a probability distribution for each of the parameters, and samples are obtained from the distributions to create random parameter sets. Derivatives of the function being analyzed are then computed at the sampled parameters and specific statistics of those derivatives are used. The paper by [Sobol and Kucherenko](https://www.sciencedirect.com/science/article/pii/S0378475409000354) discusses the relationship between the DGSM results, `tao` and `sigma` and the Morris elementary effects and Sobol Indices.

## API

```
gsa(f, method::DGSM, distr::AbstractArray; samples::Int, kwargs...)
```

  * `dist`: Array of distribution of respective variables. E.g. `dist = [Normal(5,6),Uniform(2,3)]` for two variables.

### Example

```julia
using GlobalSensitivity, Test, Distributions

samples = 2000000

f1(x) = x[1] + 2*x[2] + 6.00*x[3]
dist1 = [Uniform(4,10),Normal(4,23),Beta(2,3)]
b =  gsa(f1,DGSM(),dist1,samples=samples)
```
