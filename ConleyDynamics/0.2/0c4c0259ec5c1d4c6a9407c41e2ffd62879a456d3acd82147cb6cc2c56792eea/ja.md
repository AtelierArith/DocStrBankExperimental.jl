```
mvf_information(lc::LefschetzComplex, mvf::CellSubsets)
```

多重ベクトル場に関する基本情報を抽出します。

入力引数 `lc` はレフシェッツ複体を含み、`mvf` は多重ベクトル場を説明します。この関数は情報を `Dict{String,Any}` の形式で返します。返される辞書のキーセットを見るには、コマンド `keys` を使用できます：

  * `"N mv"`: 多重ベクトルの数
  * `"N critical"`: クリティカル多重ベクトルの数
  * `"N regular"`: レギュラー多重ベクトルの数
  * `"Lengths critical"`: クリティカル多重ベクトルの長さ分布
  * `"Lengths regular"`: レギュラー多重ベクトルの長さ分布

最後の2つの場合、辞書のエントリはペア `(length,frequency)` のベクトルであり、各ペアは `length` の長さの多重ベクトルが `frequency` 個存在することを示します。
