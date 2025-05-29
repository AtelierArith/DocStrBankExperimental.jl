```
ngwp_analysis(G::GraphSig, wavelet_packet::Array{Float64,3})
```

GraphSigオブジェクト`G`に対して、NGWP展開係数の行列を生成します。

# 入力引数

  * `G::GraphSig`: 入力GraphSigオブジェクト
  * `wavelet_packet::Array{Float64,3}`: バリマックスウェーブレットパケット。

# 出力引数

  * `dmatrix::Array{Float64,3}`: 展開係数行列。
