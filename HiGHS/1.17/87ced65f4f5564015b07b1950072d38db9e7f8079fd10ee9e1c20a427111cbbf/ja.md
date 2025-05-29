```
Highs_passLp(highs, num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value)
```

線形計画法 (LP) を HiGHS に単一の関数呼び出しで渡します。

この関数のシグネチャは [`Highs_passModel`](@ref) と同じで、二次計画法のヘッセ行列と整数ベクトルを渡すための引数は含まれていません。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
