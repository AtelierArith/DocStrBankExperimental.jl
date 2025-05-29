```
AnnuityDue(lc::LifeContingency; n=nothing, start_time=0; certain=nothing,frequency=1)
AnnuityDue(life, interest; n=nothing, start_time=0; certain=nothing,frequency=1)
```

開始時点が `start_time` で、`n` 期間後に終了する給付期間を持つ年金で、年に `1/frequency` の金額の `frequency` 回の支払いと、非偶発的な支払いを伴う `certain` 期間があります。

# 例

```
ins = AnnuityDue(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1, # 保険の期間
) 
```
