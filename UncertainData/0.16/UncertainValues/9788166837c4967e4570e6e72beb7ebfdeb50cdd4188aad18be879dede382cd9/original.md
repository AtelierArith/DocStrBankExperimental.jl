```
UncertainValue(d::Distributions.Distribution)
```

Construct an uncertain value from an instance of a distribution. If a specific uncertain value type has not been implemented, the number of parameters is  determined from the distribution and an instance of one of the following types is returned: 

  * `UncertainScalarTheoreticalOneParameter`
  * `UncertainScalarTheoreticalTwoParameter`
  * `UncertainScalarTheoreticalThreeParameter`

## Examples

```julia
UncertainValue(Normal(0, 1))
UncertainValue(Gamma(4, 5.1))
UncertainValue(Binomial, 8, 0.2)
```
