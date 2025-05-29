```
(1) details(sem_fit::SemFit; show_fitmeasures = false)

(2) details(partable::AbstractParameterTable; ...)
```

フィットしたSEMまたはパラメータテーブルに関する情報をstdoutに出力します。

# 拡張ヘルプ

## 追加のキーワード引数

  * `digits = 2`: 出力される推定値、標準誤差などの精度を制御します。
  * `color = :light_cyan`: 出力の一部の色。読みやすさのために調整できます。
  * `secondary_color = :light_yellow`
  * `show_variables = true`
  * `show_columns = nothing`: 出力に含める列名（例：`[:from, :to, :estimate]`）
