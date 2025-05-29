```
function get_structure(CNN_model::Flux.Chain, input::Array{Float32, 4})
```

畳み込みニューラルネットワークの層構造を抽出します。隠れた2次元層の正しいサイズを計算するために、入力画像が必要です。

`CNNStructure` 構造体を返します。
