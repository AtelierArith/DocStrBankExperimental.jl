```
Highs_lpCall(num_col, num_row, num_nz, a_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, col_value, col_dual, row_value, row_dual, col_basis_status, row_basis_status, model_status)
```

HiGHSを使用して線形計画法を定式化し、解決します。

### パラメータ

  * `num_col`: 列の数。
  * `num_row`: 行の数。
  * `num_nz`: 制約行列の非ゼロ要素の数。
  * `a_format`: `kHighsMatrixFormat`定数としての制約行列の形式。
  * `sense`: `kHighsObjSense`定数としての最適化の感覚。
  * `offset`: 目的定数。
  * `col_cost`: 列コストを持つ長さ[num_col]の配列。
  * `col_lower`: 列下限を持つ長さ[num_col]の配列。
  * `col_upper`: 列上限を持つ長さ[num_col]の配列。
  * `row_lower`: 行下限を持つ長さ[num_row]の配列。
  * `row_upper`: 行上限を持つ長さ[num_row]の配列。
  * `a_start`: 制約行列は、圧縮スパース列形式でHiGHSに提供されます（`a_format`が`kHighsMatrixFormatColwise`の場合、そうでなければ圧縮スパース行形式）。スパース行列は、`a_start`、`a_index`、および`a_value`の3つの配列で構成されます。`a_start`は、`a_index`内の各列の開始インデックスを含む長さ[num*col]の配列です。`a*format`が`kHighsMatrixFormatRowwise`の場合、配列は各行に対応する長さ[num_row]です。
  * `a_index`: 行列エントリのインデックスを持つ長さ[num_nz]の配列。
  * `a_value`: 行列エントリの値を持つ長さ[num_nz]の配列。
  * `col_value`: プライマル列解で埋められる長さ[num_col]の配列。
  * `col_dual`: デュアル列解で埋められる長さ[num_col]の配列。
  * `row_value`: プライマル行解で埋められる長さ[num_row]の配列。
  * `row_dual`: デュアル行解で埋められる長さ[num_row]の配列。
  * `col_basis_status`: `kHighsBasisStatus`定数の形式で列の基準状態で埋められる長さ[num_col]の配列。
  * `row_basis_status`: `kHighsBasisStatus`定数の形式で行の基準状態で埋められる長さ[num_row]の配列。
  * `model_status`: 解決後のモデルの終了状態を`kHighsModelStatus`定数の形式で配置する場所。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
