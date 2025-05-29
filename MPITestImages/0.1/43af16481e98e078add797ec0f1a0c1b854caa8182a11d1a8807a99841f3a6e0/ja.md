```julia
derenzo_image(
    diameter,
    pointSizePerSextant,
    gapBetweenSextants;
    distanceBetweenPoints,
    arrowShape
)

```

Derenzoファントムを生成する関数です。これは、ファントムの直径とファントムの各セクタのサイズ（ピクセル単位）を指定することで行われます。アルゴリズムは、半径をできるだけ多くの点で埋めることを試みます。

# 引数

  * `diameter::Int64`: ファントムの直径（ピクセル単位）。
  * `pointSizePerSextant::Vector{Integer}`: 各セクタの点のサイズ。長さは少なくとも6である必要があります。
  * `gapBetweenSextants::Union{Int64, Vector{Int64}}`: ファントムの中心とセクタの間の隙間。

# オプション引数

`distanceBetweenPoints::Union{Int64, Vector{Int64}}=-1`: 穴の間隔のctc距離。 `arrowShape::Bool=false`: trueの場合、各セクタの最後の行には、フィットする場合に穴が1つ少ない別の行があります。

# 戻り値

  * `image::Matrix{Float64}`: 結果のDerenzoファントム。

# 例

この呼び出しは、QRMのミニDerenzoファントムに似たファントムを生成します：

```
derenzo = derenzo_image(600, 
	Int.(round.([0.6*500, 0.8*500, 1.0*500, 1.2*500, 1.5*500, 2.0*500]./29)), 
	30,
	distanceBetweenPoints=Int.(round.([1.2*500, 1.6*500, 2.0*500, 2.4*500, 3.0*500, 4.0*500]./29)),
	arrowShape=true)
```
