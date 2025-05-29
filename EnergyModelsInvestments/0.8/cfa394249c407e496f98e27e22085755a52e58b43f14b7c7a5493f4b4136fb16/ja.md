```
ContinuousInvestment <: Investment
```

下限と上限の間の継続的な投資。

# フィールド

  * **`min_add::TimeProfile`** は、投資期間における最小追加容量です。`ContinuousInvestment` の場合、これはモデルが各投資期間においてこの容量以上を**必ず**投資しなければならないことを意味します。
  * **`max_add::TimeProfile`** は、投資期間における最大追加容量です。
