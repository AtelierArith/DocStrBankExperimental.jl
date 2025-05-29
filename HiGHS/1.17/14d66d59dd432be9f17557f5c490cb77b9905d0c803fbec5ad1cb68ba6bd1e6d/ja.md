```
Highs_changeColsBoundsBySet(highs, num_set_entries, set, lower, upper)
```

インデックスの配列によって指定された複数の列の境界を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_set_entries`: 変更する列の数。
  * `set`: 変更する列のインデックスを持つサイズ [num*set*entries] の配列。
  * `lower`: 新しい下限を持つ長さ [num*set*entries] の配列。
  * `upper`: 新しい上限を持つ長さ [num*set*entries] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
