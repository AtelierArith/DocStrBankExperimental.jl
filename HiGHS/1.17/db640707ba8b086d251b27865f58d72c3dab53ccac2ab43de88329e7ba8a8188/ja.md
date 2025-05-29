```
Highs_getBasicVariables(highs, basic_variables)
```

基本的な実行可能解の基底行列 $B$ を構成する行と列のインデックスを取得します。

非負のエントリは列のインデックスであり、負のエントリは `-row_index - 1` です。例えば、`{1, -1}` は2列目と1行目を示します。

これらの行と列の順序は、関数呼び出しにとって重要です：

  * [`Highs_getBasisInverseRow`](@ref) - [`Highs_getBasisInverseCol`](@ref) - [`Highs_getBasisSolve`](@ref) - [`Highs_getBasisTransposeSolve`](@ref) - [`Highs_getReducedRow`](@ref) - [`Highs_getReducedColumn`](@ref)

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `basic_variables`: 基本変数のインデックスで埋められたサイズ [num_rows] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
