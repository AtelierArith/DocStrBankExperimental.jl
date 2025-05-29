SiteTypeは、IndexタグをJulia型に変換することを可能にするパラメータ化された型です。使用例には、特定のタグを持つIndexオブジェクトに関連するカスタム演算子、Index配列、およびIndexValsを生成する`op`、`siteinds`、`state`などの関数のオーバーロードが含まれます。

SiteType型を作成するには、文字列マクロ表記を使用できます: `SiteType"MyTag"`

SiteType値またはオブジェクトを作成するには、次の表記を使用できます: `SiteType("MyTag")`

現在、`jl`によって認識されるいくつかの組み込みサイトタイプがあります。このシステムはユーザーによって簡単に拡張可能です。既存のサイトタイプに新しい演算子を追加するか、新しいサイトタイプを作成するには、[こちら](https://docs.itensor.org/ITensorMPS/stable/examples/Physics.html)の指示に従ってください。

現在の組み込みサイトタイプは次のとおりです:

  * `SiteType"S=1/2"` (または `SiteType"S=½"`)
  * `SiteType"S=1"`
  * `SiteType"Qubit"`
  * `SiteType"Qudit"`
  * `SiteType"Boson"`
  * `SiteType"Fermion"`
  * `SiteType"tJ"`
  * `SiteType"Electron"`

# 例

インデックスのタグは内部的にSiteTypesに変換され、その後、`op`や`siteind`のような関数のオーバーロードを検索します。例えば:

```julia
julia> s = siteind("S=1/2")
(dim=2|id=862|"S=1/2,Site")

julia> @show op("Sz", s);
op(s, "Sz") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.5   0.0
 0.0  -0.5

julia> @show op("Sx", s);
op(s, "Sx") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.0  0.5
 0.5  0.0

julia> @show op("Sy", s);
op(s, "Sy") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Complex{Float64},Array{Complex{Float64},1}}
 2×2
 0.0 + 0.0im  -0.0 - 0.5im
 0.0 + 0.5im   0.0 + 0.0im

julia> s = siteind("Electron")
(dim=4|id=734|"Electron,Site")

julia> @show op("Nup", s);
op(s, "Nup") = ITensor ord=2
Dim 1: (dim=4|id=734|"Electron,Site")'
Dim 2: (dim=4|id=734|"Electron,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 4×4
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0
```

多くの演算子が利用可能です。例えば:

  * `SiteType"S=1/2"`: `"Sz"`, `"Sx"`, `"Sy"`, `"S+"`, `"S-"`, ...
  * `SiteType"Electron"`: `"Nup"`, `"Ndn"`, `"Nupdn"`, `"Ntot"`, `"Cup"`,  `"Cdagup"`, `"Cdn"`, `"Cdagdn"`, `"Sz"`, `"Sx"`, `"Sy"`, `"S+"`, `"S-"`, ...
  * ...

内部のSiteType定義と演算子は[こちら](https://docs.itensor.org/ITensorMPS/stable/IncludedSiteTypes.html)で確認できます。
