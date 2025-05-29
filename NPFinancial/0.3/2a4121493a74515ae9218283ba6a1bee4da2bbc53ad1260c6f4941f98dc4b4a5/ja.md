```
mirr(values::AbstractVector{<:Real}, finance_rate::Real, reinvest_rate::Real)
```

キャッシュフローの系列、`finance_rate`（キャッシュフローに対して支払われる金利）および`reinvest_rate`（再投資時にキャッシュフローに対して受け取る金利）を考慮して修正内部収益率（MIRR）を計算します。
