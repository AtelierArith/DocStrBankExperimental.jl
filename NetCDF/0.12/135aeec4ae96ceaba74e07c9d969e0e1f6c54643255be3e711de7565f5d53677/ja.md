NcDim(name::String,values::AbstractVector)

`name`という名前のNetCDF次元オブジェクトを作成し、メモリ内の`values`に関連付けます。

### キーワード引数

  * `atts` 次元変数に関連付けられた属性のDict
  * `unlimited` これはレコード次元ですか、デフォルトは`false`です
