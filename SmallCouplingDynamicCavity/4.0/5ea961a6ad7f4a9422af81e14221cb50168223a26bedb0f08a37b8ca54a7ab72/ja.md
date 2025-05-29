```
EpidemicModel
```

システムのすべての情報を含む疫病モデル。

# フィールド

  * `Disease::SmallCouplingDynamicCavity.InfectionModel`: 感染モデル。現在実装されているのはSI、SIR、SIS、およびSIRS感染モデルです。
  * `G::Union{Vector{<:Graphs.AbstractGraph}, var"#s34"} where var"#s34"<:Graphs.AbstractGraph`: 接触グラフ。これは、AbstractGraph（時間に対して一定の接触グラフ）またはAbstractGraphのベクトル（時間変化する接触グラフ）である可能性があります。
  * `N::Int64`: 接触グラフのノード数。
  * `T::Int64`: 時間ステップの数。
  * `ν::Array{Float64, 3}`: 感染カップリング。これはNVxNVx(T+1)の配列であり、νᵗᵢⱼ=log(1-λᵗᵢⱼ)で、λᵗᵢⱼは時刻tにおける個体iから個体jへの感染確率です。
  * `obsmat::Matrix{Int8}`: 観測行列。これはNVx(T+1)の行列であり、obsᵗᵢは時刻tにおける個体iの観測値です：観測されていない場合は-1.0、Sの場合は0.0、Iの場合は1.0、Rの場合は2.0（SIRおよびSIRSのみ）です。
  * `converged::Bool`: アルゴリズムが収束したかどうかを確認するフラグ。
