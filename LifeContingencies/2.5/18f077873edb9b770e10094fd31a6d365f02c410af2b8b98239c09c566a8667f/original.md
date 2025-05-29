```
AnnuityImmediate(lc::LifeContingency; term=nothing, start_time=0; certain=nothing,frequency=1)
AnnuityImmediate(life, interest; term=nothing, start_time=0; certain=nothing,frequency=1)
```

Annuity immediate with the benefit period starting at `start_time` and ending after `term` periods with `frequency` payments per year of `1/frequency` amount and a `certain` period with non-contingent payments. 

# Examples

```
ins = AnnuityImmediate(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1 # term of policy
) 
```
