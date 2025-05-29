```
AnnuityImmediate(lc::LifeContingency; term=nothing, start_time=0; certain=nothing,frequency=1)
AnnuityImmediate(life, interest; term=nothing, start_time=0; certain=nothing,frequency=1)
```

`start_time`で始まり、`term`期間後に終了する給付期間を持つ即時年金で、年に`1/frequency`の金額で`frequency`回の支払いがあり、非偶発的な支払いを伴う`certain`期間があります。

# 例

```
ins = AnnuityImmediate(
    SingleLife(mortality = UltimateMortality([0.5,0.5]),issue_age = 0),
    FinanceModels.Yield.Constant(0.05),
    1 # 保険の期間
) 
```
