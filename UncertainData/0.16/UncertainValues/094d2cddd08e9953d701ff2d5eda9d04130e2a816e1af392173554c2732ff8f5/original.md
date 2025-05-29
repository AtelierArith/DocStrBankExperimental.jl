```
UncertainValue(t::Distributions.Truncated)
```

Construct an uncertain value from an instance of a distribution. If a specific uncertain value type has not been implemented, the number of parameters is  determined from the distribution and an instance of one of the following types is returned: 

  * `ConstrainedUncertainScalarValueOneParameter`
  * `ConstrainedUncertainScalarValueTwoParameter`
  * `ConstrainedUncertainScalarValueThreeParameter`

## Examples

```julia
# Normal distribution truncated to the interval [0.5, 0.7]
t = truncated(Normal(0, 1), 0.5, 0.7)
UncertainValue(t)

# Gamma distribution truncated to the interval [0.5, 3.5]
t = Truncate(Gamma(4, 5.1), 0.5, 3.5)
UncertainValue(t)

# Binomial distribution truncated to the interval [2, 7]
t = Truncate(Binomial(10, 0.4), 2, 7)
UncertainValue(t)
```
