```
asoxide(elms::Pair{Element, <:AbstractFloat}...; valences = NeXLCore.defaultValences, atomicweights::Dict{Element,<:AbstractFloat} = Dict{Element,Float64}())
asoxide(elms::Dict{Element, <:AbstractFloat}...; valences = NeXLCore.defaultValences, atomicweights::Dict{Element,<:AbstractFloat} = Dict{Element,Float64}())
```

構成元素の質量分率を `elms` に提供し、元素の酸化物形態の対応する量を計算します。これは次の質問に答えるために使用できます：これらの元素のこの量を測定した場合、各元素の酸化物形態の質量分率はどのくらいになりますか？以下の例は、アルバイトが質量で68.74% SiO₂であることを示しています。デフォルトでは、`val = NeXLCore.valences`、これは典型的な価数のセットです。`obystoichiometry(...)` も参照してください。

例：

```
julia> mat"NaAlSi3O8"
  NaAlSi3O8[Al=0.1029,Na=0.0877,Si=0.3213,O=0.4881]
julia> asoxide(n"Al"=>0.1029, n"Na"=>0.0877, n"Si"=>0.3213)
  Dict{Material, Float64} with 3 entries:
  SiO₂[O=0.5326,Si=0.4674]  => 0.687366
  Al₂O₃[Al=0.5293,O=0.4707] => 0.194424
  Na₂O[Na=0.7419,O=0.2581]  => 0.118216
julia> sum(asoxide(n"Al"=>0.1029, n"Na"=>0.0877, n"Si"=>0.3213), name="Albite")
  Albite[Al=0.1029,Na=0.0877,O=0.4881,Si=0.3213]
julia> asoxide(filter(kv->kv[1]!=n"O", massfraction(mat"NaAlSi3O8")))
  Dict{Material, Float64} with 3 entries:
    SiO₂[O=0.5326,Si=0.4674]  => 0.687401
    Al₂O₃[Al=0.5293,O=0.4707] => 0.194418
    Na₂O[Na=0.7419,O=0.2581]  => 0.118181
```
