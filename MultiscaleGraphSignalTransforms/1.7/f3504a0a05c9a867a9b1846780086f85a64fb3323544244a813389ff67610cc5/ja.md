getall*expansioncoeffs2(G*Sig::GraphSig, GP*star::GraphPart,                                  GP*star*Lsym::GraphPart,                                  VM*NGWP::Array{Float64,3},                                  PC*NGWP::Array{Float64,3},                                  LP*NGWP::Array{Float64,3},                                  VM*NGWP*Lsym::Array{Float64,3},                                  PC*NGWP*Lsym::Array{Float64,3},                                  LP*NGWP*Lsym::Array{Float64,3},                                  𝚽::Matrix{Float64},                                  𝚽sym::Matrix{Float64})

`f`のすべての展開係数を、NGWP.jlおよびMTSG.jlのすべての方法を通じて論文で取得します。

# 入力引数

  * `G_Sig::GraphSig`: プライマルグラフのGraphSig
  * `GP_star::GraphPart`: デュアルグラフのGraphPart
  * `VM_NGWP::Array{Float64,3}`: バリマックスNGWP。
  * `PC_NGWP::Array{Float64,3}`: ペアクラスタリングNGWP。
  * `LP_NGWP::Array{Float64,3}`: ラップドNGWP。
  * `VM_NGWP_Lsym::Array{Float64,3}`: バリマックスNGWPのLsymバージョン。
  * `PC_NGWP_Lsym::Array{Float64,3}`: ペアクラスタリングNGWPのLsymバージョン。
  * `LP_NGWP_Lsym::Array{Float64,3}`: ラップドNGWPのLsymバージョン。
  * `𝚽::Matrix{Float64}`: `L`の固有ベクトルの行列。
  * `𝚽sym::Matrix{Float64}`: `Lsym`の固有ベクトルの行列。
