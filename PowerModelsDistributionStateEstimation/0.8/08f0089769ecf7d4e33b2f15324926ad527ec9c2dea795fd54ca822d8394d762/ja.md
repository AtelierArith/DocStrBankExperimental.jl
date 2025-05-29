```
assign_residual_ub!(data::Dict; chosen_upper_bound::Float64=100, rescale::Bool=false)
```

残差変数に上限を割り当てる基本的な関数で、測定辞書に `"res_max"` エントリを追加します。この関数は、単一の測定辞書（例： `data["meas"]["1"]` ）または完全な測定辞書（ `data["meas]` ）のいずれかを入力として受け取ります。     # 引数     - data: フィーダーの `ENGINEERING` データモデル、または単一の測定に対応する辞書     - chosen*upper*bound: 有限の上限、指定がない場合はデフォルトで100     - rescale: デフォルトは `false`。 `true` の場合、 `chosen_upper_bound` は `data["se_settings"]["rescaler"]` の値で乗算され、その積が上限として使用されます。そうでなければ、
