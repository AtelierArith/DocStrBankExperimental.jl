```
Highs_passMip(highs, num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, integrality)
```

混合整数線形計画法（MILP）を単一の関数呼び出しでHiGHSに渡します。

関数のシグネチャは、二次計画法のヘッセ行列を渡すための引数を除いて、[`Highs_passModel`](@ref)と同一です。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
