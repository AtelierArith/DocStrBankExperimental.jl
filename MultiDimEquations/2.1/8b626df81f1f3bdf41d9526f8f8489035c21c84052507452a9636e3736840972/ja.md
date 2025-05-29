```
defLoadVars(vars, df, dimsNameCols; <keyword arguments>)
```

必要なIndexedTablesまたは配列を定義し、次元列と変数名を含む列を指定しながら、長い形式のDataFrameからデータをロードします。

`varLoadVar`のように、ここでは入力データフレームの1つの列に変数名を格納しながら、複数の変数を一度に抽出しています。

# 引数

  * `vars`: 参照する変数の配列
  * `df`: データフレームのソースで、dim1|dim2|...|varName|valueの形式でなければなりません
  * `dimsNameCols`: 変数が定義されている次元を含む列の名前
  * `varNameCol (def: "varName")`: df内の変数名を含む列の名前
  * `valueCol (def: "value")`: df内の値を含む列の名前
  * `sparse (def: "true")`: `NDSparse`要素（IndexedTableから）または標準配列を返すかどうか
  * `missingValue` (def=`missing`): 行列をどのように埋めるか（配列にのみ関連）
  * `fullKeys` (def=`true`): 出力されるすべての変数が完全なキーのセットに基づくべきか、フィルタリングされた入力データフレームで特に見つかったキーのそれぞれを探すべきかどうか

# 注意事項

  * スパースインデックステーブルは要素ごとにアクセスできますが、遅く、標準配列は位置ごとにアクセスする必要がありますが、速いです
  * 現在、`sameKeys=true`は非スパースの場合にのみ実装されています

# 例

```julia
julia> (vol,numberOfTrees)  = defVars(["vol","numberOfTrees"], forestData,["region","treeSpecie","year"], varNameCol="parName", valueCol="value")
```
