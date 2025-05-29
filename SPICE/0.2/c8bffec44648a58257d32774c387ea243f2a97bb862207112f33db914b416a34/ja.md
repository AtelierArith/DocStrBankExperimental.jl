```
stpool(item, nth, contin, lenout=1024)
```

カーネルプール変数から nth 番目の文字列を取得します。この文字列は、カーネルプール変数のいくつかのコンポーネントにまたがって続く場合があります。

### 引数

  * `item`: カーネルプール変数の名前
  * `nth`: 取得するフル文字列のインデックス
  * `contin`: 続きを示すために使用される文字列
  * `lenout`: 出力文字列の利用可能なスペース（デフォルト: 1024）

### 出力

カーネル変数が見つかった場合は、続きにわたって連結されたフル文字列を返し、そうでない場合は `nothing` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/stpool_c.html)
