```
getall_expansioncoeffs(G_Sig::GraphSig, GP_star::GraphPart, VM_NGWP::Array{Float64,3}, PC_NGWP::Array{Float64,3}, 𝚽::Matrix{Float64})
```

`f`のすべての展開係数をNGWP.jlおよびMTSG.jlのすべての方法を通じて取得します。

# 入力引数

  * `G_Sig::GraphSig`: プライマルグラフのGraphSig
  * `GP_star::GraphPart`: デュアルグラフのGraphPart
  * `VM_NGWP::Array{Float64,3}`: バリマックスNGWP。
  * `PC_NGWP::Array{Float64,3}`: ペアクラスタリングNGWP。
  * `𝚽::Matrix{Float64}`: グラフラプラシアン固有ベクトルの行列。
