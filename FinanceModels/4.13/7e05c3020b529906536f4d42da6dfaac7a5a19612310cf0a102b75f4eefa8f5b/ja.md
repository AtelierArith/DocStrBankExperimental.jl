```
present_value(model,contract,current_time=0.0)
present_value(model,projection,current_time=0.0)
```

与えられた契約または `CashflowProjection` 型のプロジェクションに対して、`model` に埋め込まれた評価仮定に対応する契約の価値を返します。

# 例

```julia
m = Equity.BlackScholesMerton(0.01, 0.02, 0.15)

a = Option.EuroCall(CommonEquity(), 1.0, 1.0)

pv(m, a) # ≈ 0.05410094201902403
```
