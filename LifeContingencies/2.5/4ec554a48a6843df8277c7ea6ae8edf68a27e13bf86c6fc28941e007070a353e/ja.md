```
Insurance(lc::LifeContingency, term)
Insurance(life,interest, term)
Insurance(lc::LifeContingency)
Insurance(life,interest)
```

`term`の期間を持つ生命保険。`term`が`nothing`の場合、終身保険となります。

発行年齢は、LifeContingency `lc`の`issue_age`に基づいています。

# 例

```
ins = Insurance(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1           # 1年の期間
) 
```
