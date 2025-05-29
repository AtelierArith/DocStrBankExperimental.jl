```
isoinvset_information(lc::LefschetzComplex, mvf::CellSubsets, iis::Cells)
```

孤立不変集合に関する基本情報を計算します。

入力引数 `lc` にはレフシェッツ複体が含まれ、`mvf` は多重ベクトル場を説明します。孤立不変集合は引数 `iis` で指定されます。この関数は情報を `Dict{String,Any}` の形式で返します。コマンド `keys` を使用して返された辞書のキーセットを見ることができます。これらは以下の情報を説明します：

  * `"Conley index"` には孤立不変集合のコンリー指数が含まれます。
  * `"N multivectors"` には孤立不変集合内の多重ベクトルの数が含まれます。
