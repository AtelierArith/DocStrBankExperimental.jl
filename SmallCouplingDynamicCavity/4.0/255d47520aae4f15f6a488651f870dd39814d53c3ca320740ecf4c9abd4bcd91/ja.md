```
EpidemicModel(
    infectionmodel::TI, 
    G::TG, T::Int, 
    ν::Array{Float64, 3}, 
    obs::Matrix{Int8}) where {TI<:InfectionModel,TG<:AbstractGraph}
```

疫病モデルを定義します。

この関数は、提供された感染モデル、接触グラフ、時間ステップ、感染結合、および観察行列に基づいて疫病モデルを定義します。

# 引数

  * `infectionmodel`: 感染モデル。現在実装されているモデルには、SI、SIR、SIS、およびSIRS感染モデルが含まれます。
  * `G`: 接触グラフ。時間変化する接触グラフを表すAbstractGraphである必要があります。
  * `T`: 時間ステップの数。
  * `ν`: 感染結合。サイズがNVxNVx(T+1)の3次元配列である必要があり、νᵗᵢⱼ=log(1-λᵗᵢⱼ)で、λᵗᵢⱼは時刻tにおける個人iから個人jへの感染確率です。
  * `obs`: 観察行列。サイズがNVx(T+1)の行列である必要があり、obsᵗᵢは時刻tにおける個人iの観察値です：観察されていない場合は-1.0、Sの場合は0.0、Iの場合は1.0、Rの場合は2.0（SIRおよびSIRSのみ）です。

# 戻り値

  * `EpidemicModel`: 定義された疫病モデルを表す[`EpidemicModel`](@ref)オブジェクト。
