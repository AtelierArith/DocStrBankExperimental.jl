```
Highs_passModel(highs, num_col, num_row, num_nz, q_num_nz, a_format, q_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, q_start, q_index, q_value, integrality)
```

HiGHSにモデルを単一の関数呼び出しで渡します。これは、[`Highs_addRow`](@ref)および[`Highs_addCol`](@ref)を使用してモデルを構築するよりも高速です。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `num_col`: 列の数。
  * `num_row`: 行の数。
  * `num_nz`: 制約行列の要素数。
  * `q_num_nz`: ヘッセ行列の要素数。
  * `a_format`: `kHighsMatrixFormat`定数の形式で使用する制約行列の形式。
  * `q_format`: `kHighsHessianFormat`定数の形式で使用するヘッセ行列の形式。
  * `sense`: `kHighsObjSense`定数の形式での最適化の感覚。
  * `offset`: 目的関数の定数項。
  * `col_cost`: 目的係数を持つ長さ[num_col]の配列。
  * `col_lower`: 下限列境界を持つ長さ[num_col]の配列。
  * `col_upper`: 上限列境界を持つ長さ[num_col]の配列。
  * `row_lower`: 上限行境界を持つ長さ[num_row]の配列。
  * `row_upper`: 上限行境界を持つ長さ[num_row]の配列。
  * `a_start`: 制約行列は、圧縮スパース列形式でHiGHSに提供されます（`a_format`が`kHighsMatrixFormatColwise`の場合、そうでなければ圧縮スパース行形式）。スパース行列は、`a_start`、`a_index`、および`a_value`の3つの配列で構成されます。`a_start`は、`a_index`内の各列の開始インデックスを含む長さ[num*col]の配列です。`a*format`が`kHighsMatrixFormatRowwise`の場合、配列は各行に対応する長さ[num_row]です。
  * `a_index`: 行列のエントリのインデックスを持つ長さ[num_nz]の配列。
  * `a_value`: 行列のエントリの値を持つ長さ[num_nz]の配列。
  * `q_start`: ヘッセ行列は、圧縮スパース列形式で下三角成分としてHiGHSに提供されます（または、同等に、圧縮スパース行形式で上三角成分として）。スパース行列は、`q_start`、`q_index`、および`q_value`の3つの配列で構成されます。`q_start`は長さ[num_col]の配列です。モデルが線形の場合はNULLを渡します。
  * `q_index`: 行列のエントリのインデックスを持つ長さ[q*num*nz]の配列。モデルが線形の場合はNULLを渡します。
  * `q_value`: 行列のエントリの値を持つ長さ[q*num*nz]の配列。モデルが線形の場合はNULLを渡します。
  * `integrality`: 各列に対する`kHighsVarType`定数を含む長さ[num_col]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
