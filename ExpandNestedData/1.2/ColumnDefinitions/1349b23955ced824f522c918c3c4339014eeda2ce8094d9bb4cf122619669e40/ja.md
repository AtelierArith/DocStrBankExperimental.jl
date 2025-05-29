```
ColumnDefinition(field_path; column_name=nothing, flatten_arrays=false, default_value=missing, pool_arrays=false)
```

## 引数

  * `field_path`: データの最上部から列の値を抽出するためのキー/フィールド名のベクターまたはタプル

## キーワード引数

  * `column_name::Symbol`: 結果の列の名前。`nothing`の場合、`field_path`をスネークケース形式で結合したものがデフォルトとなります。
  * `default_value`: field_pathのキーが1つ以上のブランチに存在しない場合、この値で埋めます。デフォルト: `missing`
  * `pool_arrays::Bool`: この列の値を収集する際に、`Base.Vector`の代わりに`PooledArrays`を使用するかどうかを選択します。デフォルト: `false`（`Vector`を使用）
  * `name_join_pattern::String`: フィールドパスを列名に結合するためのセパレーター。デフォルト: "_"

## 戻り値

`::ColumnDefinition`
