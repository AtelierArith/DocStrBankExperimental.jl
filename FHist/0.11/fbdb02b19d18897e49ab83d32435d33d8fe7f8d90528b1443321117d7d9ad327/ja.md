# **空の** ヒストグラムを作成する

all-keyword-arguments コンストラクタを使用します:

```julia
FHist.Hist1D(;
    counttype=Float64,
    binedges::E
    bincounts = zeros(counttype, length.(_to_tuple(binedges)) .- 1),
    sumw2 = zero(bincounts),
    nentries = 0
    overflow::Bool = false
) where {E<:NTuple{1,Any}}
```

!!! note
    `binedges` 以外はすべてオプションです（`binedges` から推測されます）。


# データ（および重みなど）を指定してヒストグラムを作成する

データのための位置引数と残りのためのキーワード引数を使用します:

```julia
FHist.Hist1D(array::E;
    counttype=Float64,
    binedges=nothing,
    weights=nothing,
    nbins=nothing,
    overflow=false)
) where {E<:NTuple{1,Any}}
```

!!! note
    データ（`array`）以外はすべてオプションです（データから推測されます）。

