```
Highs_mipCall(num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, integrality, col_value, row_value, model_status)
```

HiGHSを使用して混合整数線形計画法を定式化し、解決します。

このメソッドのシグネチャは[`Highs_lpCall`](@ref)と同じですが、追加の`integrality`引数があり、`col_dual`、`row_dual`、`col_basis_status`および`row_basis_status`引数が欠けています。

### パラメータ

  * `integrality`: 各列に対する`kHighsVarType`定数を含む長さ[num_col]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
