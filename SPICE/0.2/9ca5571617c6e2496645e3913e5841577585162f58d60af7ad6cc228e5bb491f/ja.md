```
timout(et, pictur, lenout=128)
```

このルーチンは、TDB秒で表された入力エポックをJ2000のTDBエポックからの秒数に変換し、ユーザーのフォーマットピクチャの仕様に従ってフォーマットされた文字列を生成します。

### 引数

  * `et`: エフェメリスエポックJ2000からの秒数で表されたエポック
  * `pictur`: 出力文字列のフォーマット仕様
  * `lenout`: 出力文字列の長さに1を加えたもの（デフォルト: 128）

### 出力

入力エポックの文字列表現を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/timout_c.html)
