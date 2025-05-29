```
struct SingleLife
    mortality
    issue_age::Int
    alive::Bool
    fractional_assump::MortalityTables.DeathDistribution
end
```

A `Life` object containing the necessary assumptions for contingent maths related to a single life. Use with a `LifeContingency` to do many actuarial present value calculations. 

Keyword arguments:

  * `mortality` pass a mortality vector, which is an array of applicable mortality rates indexed by attained age
  * `issue_age` is the assumed issue age for the `SingleLife` and is the basis of many contingency calculations.
  * `alive` Default value is `true`. Useful for joint insurances with different status on the lives insured.
  * `fractional_assump`. Default value is `Uniform()`. This is a `DeathDistribution` from the `MortalityTables.jl` package and is the assumption to use for non-integer ages/times.

# Examples

```
using MortalityTables
mortality = MortalityTables.table("2001 VBT Residual Standard Select and Ultimate - Male Nonsmoker, ANB")

SingleLife(
    mort       = mort.select[30], 
    issue_age  = 30          
)
```
