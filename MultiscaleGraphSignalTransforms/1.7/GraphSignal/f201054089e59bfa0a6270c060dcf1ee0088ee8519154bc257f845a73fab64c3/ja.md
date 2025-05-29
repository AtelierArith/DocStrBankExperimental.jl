```
function AddNoise(G::GraphSig; SNR::Float64=Float64(1.24), noisetype::String = "gaussian")
```

GraphSigオブジェクトのデータにノイズを追加します

### 入力引数

  * `G::GraphSig`: GraphSigオブジェクト
  * `SNR`: ノイズのある信号が持つべきSNR
  * `noisetype`: ノイズの種類: ガウス（デフォルト）またはポアソン

### 出力引数

  * `G::GraphSig`: ノイズが追加されたGraphSigオブジェクト
  * `sigma`: ノイズの標準偏差
