```
Highs_qpCall(num_col, num_row, num_nz, q_num_nz, a_format, q_format, sense, offset, col_cost, col_lower, col_upper, row_lower, row_upper, a_start, a_index, a_value, q_start, q_index, q_value, col_value, col_dual, row_value, row_dual, col_basis_status, row_basis_status, model_status)
```

HiGHSを使用して二次計画問題を定式化し、解決します。

このメソッドのシグネチャは[`Highs_lpCall`](@ref)と同じですが、ヘッセ行列を指定するための追加の引数があります。

### パラメータ

  * `q_num_nz`: ヘッセ行列の非ゼロ要素の数。
  * `q_format`: ヘッセ行列の形式を`kHighsHessianStatus`定数の形で指定します。q*num*nz > 0の場合、これは`kHighsHessianFormatTriangular`でなければなりません。
  * `q_start`: ヘッセ行列は、圧縮スパース列形式で下三角成分としてHiGHSに提供されます（または、同等に、圧縮スパース行形式で上三角成分として提供されます）。スパース行列は、`q_start`、`q_index`、および`q_value`の3つの配列で構成されます。`q_start`は長さ[num_col]の配列です。
  * `q_index`: 行列のエントリのインデックスを持つ長さ[q*num*nz]の配列。
  * `q_value`: 行列のエントリの値を持つ長さ[q*num*nz]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
