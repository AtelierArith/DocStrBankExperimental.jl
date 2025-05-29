```
Highs_getColsByRange(highs, from_col, to_col, num_col, costs, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

モデルから隣接する複数の列に関連するデータを取得します。

制約係数を照会するには、この関数を2回呼び出す必要があります。

最初に、`matrix_start`、`matrix_index`、および`matrix_value`を`NULL`としてこの関数を呼び出します。この呼び出しは、制約行列の対応するセクションにおける非ゼロ要素の数である`num_nz`を設定します。

次に、`num_nz`の長さの新しい`matrix_index`および`matrix_value`配列を割り当て、この関数を再度呼び出して新しい配列にその内容を設定します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `from_col`: データを照会する最初の列。
  * `to_col`: データを照会する最後の列（含む）。
  * `num_col`: モデルから取得した列の数で設定される整数（これは`to\_col - from\_col + 1`に等しい必要があります）。
  * `costs`: 列のコスト係数用のサイズ[to*col - from*col + 1]の配列。
  * `lower`: 列の下限用のサイズ[to*col - from*col + 1]の配列。
  * `upper`: 列の上限用のサイズ[to*col - from*col + 1]の配列。
  * `num_nz`: 制約行列の非ゼロ要素の数で設定される整数。
  * `matrix_start`: `matrix_index`および`matrix_value`内の各列の開始インデックスを持つサイズ[to*col - from*col + 1]の配列。
  * `matrix_index`: 制約行列内の各要素の行インデックスを持つサイズ[num_nz]の配列。
  * `matrix_value`: 制約行列の非ゼロ要素を持つサイズ[num_nz]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
