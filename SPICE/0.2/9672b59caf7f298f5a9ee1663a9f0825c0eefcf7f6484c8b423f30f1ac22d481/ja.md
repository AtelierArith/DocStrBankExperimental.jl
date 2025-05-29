```
gnpool(name, start, room, lenout=128)
```

指定されたテンプレートに一致するカーネル変数の名前を返します。

### 引数

  * `name`: 名前が一致する必要があるテンプレート
  * `start`: 取得する最初の一致する名前のインデックス
  * `room`: 返す値の最大数
  * `lenout`: 出力配列 `kvars` の文字列の長さ (デフォルト: 128)

### 出力

`name` に一致するカーネルプール変数の名前を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gnpool_c.html)
