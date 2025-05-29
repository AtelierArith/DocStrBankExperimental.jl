```
AnnuityDue(lc::LifeContingency; n=nothing, start_time=0; certain=nothing,frequency=1)
AnnuityDue(life, interest; n=nothing, start_time=0; certain=nothing,frequency=1)
```

Annuity due with the benefit period starting at `start_time` and ending after `n` periods with `frequency` payments per year of `1/frequency` amount and a `certain` period with non-contingent payments. 

# Examples

```
ins = AnnuityDue(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1, # term of policy
) 
```
