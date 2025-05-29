```
Highs_getRowByName(highs, name, row)
```

名前から行のインデックスを取得します。

複数の行が同じ名前を持っている場合、または`name`に該当する行が存在しない場合、この関数は`kHighsStatusError`を返します。

### パラメータ

  * `name`: クエリする行の名前のポインタ。
  * `row`: 行のインデックスを格納するポインタ。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
