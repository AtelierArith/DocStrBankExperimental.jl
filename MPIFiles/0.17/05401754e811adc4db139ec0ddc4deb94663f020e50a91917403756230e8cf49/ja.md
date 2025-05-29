```
loadTDesign(t::Int64, N::Int64, radius::S=10Unitful.mm, center::Vector{V}=[0.0,0.0,0.0]Unitful.mm, filename::String=joinpath(@__DIR__, "TDesigns.hd5")) where {S,V<:Unitful.Length}
```

*説明:* 選択した次数 t と点の数 N の t-デザイン配列を返します。

*入力:*

  * `t` - 次数
  * `N` - 点の数
  * `radius` - 球の半径 (デフォルト: 10mm)
  * `center` - 球の中心 (デフォルト: [0.0,0.0,0.0]mm)
  * `filename` - t-デザインを含むファイルの名前 (デフォルトで TDesign.hd5 を読み込みます)

*出力:*

  * t、半径、中心、および位置を含む直交座標系の SphericalTDesign 型の t-デザイン (位置は `getindex(tdes,i)` が使用されない限り単位球上にあります)
