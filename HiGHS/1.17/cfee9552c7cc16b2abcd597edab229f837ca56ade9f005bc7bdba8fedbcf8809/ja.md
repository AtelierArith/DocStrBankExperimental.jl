```
Highs_getPresolvedLp(highs, a_format, num_col, num_row, num_nz, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, integrality)
```

HiGHSの事前解決されたLPからデータを取得します。

入力引数は、[`Highs_passModel`](@ref)で使用されるものと同じ意味を持ちます（異なる順序で）。

すべての配列は、[`Highs_getModel`](@ref)を呼び出す前に正しいサイズに事前に割り当てられている必要があります。適切なサイズを確認するために、次のクエリメソッドを使用してください: - [`Highs_getPresolvedNumCol`](@ref) - [`Highs_getPresolvedNumRow`](@ref) - [`Highs_getPresolvedNumNz`](@ref)

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。 ```
