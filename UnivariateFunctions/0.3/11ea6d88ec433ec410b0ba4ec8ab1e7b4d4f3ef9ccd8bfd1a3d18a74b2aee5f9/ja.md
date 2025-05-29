```
period_length(a::Dates.DatePeriod, base::Date = global_base_date)
```

期間の長さは、`TimePeriod`オブジェクトを`years_from_global_base`に一貫した方法で変換するように設計されています。したがって、実際には`years_between`メソッドは、`Dates.DatePeriod`の開始日と終了日を使用して計算されます。これは、`Month(3)`のような期間が、年のどの時期であるかによって総日数がわずかに異なる可能性があるため、少し複雑です。したがって、基準日を入力する必要があります。この基準日から期間が測定されます。

### 入力

  * `period` - 期間。
  * `base` - 期間が測定される日付。

### 戻り値

  * `Real`。
