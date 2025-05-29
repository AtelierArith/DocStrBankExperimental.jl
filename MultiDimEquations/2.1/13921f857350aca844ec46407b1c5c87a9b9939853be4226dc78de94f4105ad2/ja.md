```
defLoadVar(df, dimsNameCols; <keyword arguments>)
```

必要なIndexedTablesまたは配列を定義し、次元列を指定しながら長い形式のDataFrameからデータをロードします。

# 引数

  * `df`: データフレームのソースで、dim1|dim2|...|valueの形式でなければなりません
  * `dimsNameCols`: 変数が定義されている次元に対応する列の名前（キー）
  * `valueCol (def: "value")`: df内の値を含む列の名前
  * `sparse (def: "true")`: `NDSparse`要素（IndexedTableから）または標準配列を返すかどうか
  * `missingValue` (def=`missing`): 行列をどのように埋めるか（配列にのみ関連）

# 注意事項

  * スパースインデックス付きテーブルは要素ごとにアクセスできますが遅く、標準配列は位置ごとにアクセスする必要がありますが速いです

# 例

```julia
julia> vol  = defVars(volumeData,["region","treeSpecie","year"], valueCol="value")
```
