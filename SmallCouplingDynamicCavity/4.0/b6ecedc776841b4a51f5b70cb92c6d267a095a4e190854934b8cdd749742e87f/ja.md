```
EpidemicModel(
    infectionmodel::TI, 
    G::TG, T::Int, 
    ν::Array{Float64, 3}) where {TI<:InfectionModel,TG<:Vector{<:AbstractGraph}}
```

疫病モデルを定義します。

この関数は、提供された感染モデル、時間変化する接触グラフ、時間ステップ、および感染結合に基づいて疫病モデルを定義します。観測行列をゼロで初期化します。

# 引数

  * `infectionmodel`: 感染モデル。現在実装されているモデルには、SI、SIR、SIS、およびSIRS感染モデルが含まれます。
  * `G`: 接触グラフ。時間変化する接触グラフを表すAbstractGraphのT+1ベクトルである必要があります。
  * `T`: 時間ステップの数。
  * `ν`: 感染結合。サイズがNVxNVx(T+1)の3次元配列である必要があり、νᵗᵢⱼ=log(1-λᵗᵢⱼ)で、λᵗᵢⱼは時刻tにおける個人iから個人jへの感染確率です。

# 戻り値

  * `EpidemicModel`: 定義された疫病モデルを表す[`EpidemicModel`](@ref)オブジェクト。
