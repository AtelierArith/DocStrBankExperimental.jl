This function represents the numeric support of the distribution and return a tuple `(float_start::Float, float_stop::Float)`. The default value is: `(1e-4, 10_000)`. Note that some distributions are not defined at `0` i.e. Weibull with shape parameter less than 1.

The pdf and hazard are 0 before `float_start` and the numeric integration to calculate the integral over the haazrd in `cumulative_hazard` starts at `beginning`. When sampling with `rand` an ODE is solved over the support.

# Usage

You should adjust the support according to your data

```julia
JointSurvivalModels.support(dist:HazardBasedDistribution) = (-100, 1000)
```
