```
struct JointLife
    lives
    contingency
    joint_assumption
end

A `Life` object containing the necessary assumptions for contingent maths related to a joint life insurance. Use with a `LifeContingency` to do many actuarial present value calculations.
```

Keyword arguments:

  * `lives` is a tuple of two `SingleLife`s
  * `contingency` default is `LastSurvivor()`. It is the trigger for contingent benefits. See `?Contingency`.
  * `joint_assumption` Default value is `Frasier()`. It is the assumed relationship between the mortality of the two lives. See `?JointAssumption`.

# Examples

```
using MortalityTables
mortality = MortalityTables.table("2001 VBT Residual Standard Select and Ultimate - Male Nonsmoker, ANB")

l1 = SingleLife(
    mortality       = mortality.select[30], 
    issue_age  = 30          
)
l2 = SingleLife(
    mortality       = mortality.select[30], 
    issue_age  = 30          
)

jl = JointLife(
    lives = (l1,l2),
    contingency = LastSurvivor(),
    joint_assumption = Frasier()
)
```
