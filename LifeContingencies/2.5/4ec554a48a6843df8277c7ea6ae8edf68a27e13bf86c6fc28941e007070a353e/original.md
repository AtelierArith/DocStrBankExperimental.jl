```
Insurance(lc::LifeContingency, term)
Insurance(life,interest, term)
Insurance(lc::LifeContingency)
Insurance(life,interest)
```

Life insurance with a term period of `term`. If `term` is `nothing`, then whole life insurance.

Issue age is based on the `issue_age` in the LifeContingency `lc`.

# Examples

```
ins = Insurance(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1           # 1 year term
) 
```
