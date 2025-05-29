```
volatility(ito::ItoSet, ito_integral_id::Symbol, on::Union{Date,DateTime})
```

指定した日付の`ito_integral`のボラティリティを取得します。

### 入力

  * `ito` - ボラティリティを取得したい`ItoSet`。
  * `ito_integral_id` - 興味のあるito辞書のキー。
  * `on` - ボラティリティを取得したい時間または瞬間。

### 戻り値

  * スカラー
