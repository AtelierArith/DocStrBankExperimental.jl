```
UncertainScalarPopulation(values, probs)
UncertainScalarPopulation(values, probs::Vector{Number})
UncertainScalarPopulation(values, probs::Statsbase.AbstractWeights)
```

An `UncertainScalarPopulation`, which consists of some population members (`values`) and some weights (`probs`) that indicate the relative importance of the  population members (for example during resampling). 

## Fields

  * **`values`**: The members of the population. Can be either numerical values, any   type of uncertain value defined in this package (including populations), and   `Measurement` instances from Measurements.jl.
  * **`probs`**: The probabilities of sampling each member of the population.

## Constructors

  * If `values` contains only scalar numeric values, then the `values` field    will be of type `Vector{Number}`.
  * If `values` contains one or more uncertain values, then the `values` field    will be of type `Vector{AbstractUncertainValue}`

## Example

```julia

# Uncertain population consisting of CertainValues (scalars get promoted to 
# CertainValue), theoretical distributions and KDE distributions
pop1 = UncertainScalarPopulation(
    [3.0, UncertainValue(Normal, 0, 1), UncertainValue(Gamma, 2, 3), 
    UncertainValue(Uniform, rand(1000))], [0.5, 0.5, 0.5, 0.5])

# Uncertain population consisting of scalar values
pop2 = UncertainScalarPopulation([1, 2, 3], rand(3))
pop3 = UncertainScalarPopulation([1, 2, 3], Weights(rand(3)))

# Uncertain population consisting of uncertain populations
pop4 = UncertainScalarPopulation([pop1, pop2], [0.1, 0.5])

# Uncertain population consisting of uncertain populations, a scalar and 
# a normal distribution. Assign random weights.
vals = [pop1, pop2, 2, UncertainValue(Normal, 0.3, 0.014)]
pop5 = UncertainScalarPopulation(vals, Weights(rand(4)))
```
