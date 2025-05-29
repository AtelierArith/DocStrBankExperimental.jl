```
nccreate (filename, varname, dimensions ...)
```

既存のNetCDFファイルに変数を作成するか、新しいファイルを生成します。`filename`と`varname`は文字列です。その後に次元のリストが続きます。各次元エントリは次元名（文字列）で始まり、次元の長さ、次元値の配列、または次元属性を含むDictが続く場合があります。次の次元が入力され、そのように続きます。例としてexamples/high.jlを参照してください。

### キーワード引数

  * **atts** 作成された変数に割り当てる属性名と値のDict
  * **gatts** グローバル属性として書き込む属性名と値のDict
  * **compress** ファイルの圧縮レベルを設定する整数[0..9]、`mode=NC_NETCDF4`の場合のみ有効
  * **t** 変数の型、現在サポートされている型は：定数 `NC_BYTE`、`NC_CHAR`、`NC_SHORT`、`NC_INT`、`NC_FLOAT`、`NC_LONG`、`NC_DOUBLE`
  * **mode** ファイル作成モード、新しいファイルが作成されるときのみ有効、次のいずれかを選択：`NC_NETCDF4`、`NC_CLASSIC_MODEL`、`NC_64BIT_OFFSET`
