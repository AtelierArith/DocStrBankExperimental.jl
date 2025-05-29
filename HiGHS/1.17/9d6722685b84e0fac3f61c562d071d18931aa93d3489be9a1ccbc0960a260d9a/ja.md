```
Highs_passHessian(highs, dim, num_nz, format, start, index, value)
```

二次目的のためのヘッセ行列を設定します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `dim`: ヘッセ行列の次元。 [num_col]である必要があります。
  * `num_nz`: ヘッセ行列の非ゼロ要素の数。
  * `format`: `kHighsHessianFormat`定数としてのヘッセ行列のフォーマット。この値は`kHighsHessianFormatTriangular`でなければなりません。
  * `start`: ヘッセ行列は、`q_start`、`q_index`、および`q_value`を使用して、圧縮スパース列形式（または同等に、圧縮スパース行形式の上三角成分）としてHiGHSに提供されます。ヘッセ行列は、圧縮スパース列形式の下三角成分としてHiGHSに提供されます。スパース行列は、`start`、`index`、および`value`の3つの配列で構成されています。`start`は、`index`内の各列の開始インデックスを含む長さ[num_col]の配列です。
  * `index`: 行列のエントリのインデックスを持つ長さ[num_nz]の配列。
  * `value`: 行列のエントリの値を持つ長さ[num_nz]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
