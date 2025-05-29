```
Highs_changeColsCostBySet(highs, num_set_entries, set, cost)
```

複数の列のコストを、インデックスの配列によって変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_set_entries`: 変更する列の数。
  * `set`: 変更する列のインデックスを持つサイズ [num*set*entries] の配列。
  * `cost`: 列の新しいコストを持つ長さ [num*set*entries] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
