```
NcDim(name::String,dimlength::Integer)
```

メモリ内に長さ `dimlength` の `name` という名前の NetCDF 次元オブジェクトを作成します。

### キーワード引数

  * `values=[]` 次元変数に書き込むことができる次元値を追加するためのオプション
  * `atts` 次元変数に関連付けられた属性の Dict
  * `unlimited` これはレコード次元ですか、デフォルトは `false` です
