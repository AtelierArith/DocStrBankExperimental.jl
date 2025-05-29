```
Highs_getColByName(highs, name, col)
```

列の名前からインデックスを取得します。

同じ名前の列が複数ある場合や、`name` に該当する列が存在しない場合、この関数は `kHighsStatusError` を返します。

### パラメータ

  * `name`: クエリする列の名前のポインタ。
  * `col`: 列のインデックスを格納するポインタ。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
