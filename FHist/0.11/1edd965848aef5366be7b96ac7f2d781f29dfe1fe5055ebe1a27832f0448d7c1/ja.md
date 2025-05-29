# **空の** ヒストグラムを作成する

すべてのキーワード引数コンストラクタを使用します：

```julia
FHist.Hist2D(;
    counttype=Float64,
    binedges::E
    bincounts = zeros(counttype, length.(_to_tuple(binedges)) .- 1),
    sumw2 = zero(bincounts),
    nentries = 0
    overflow::Bool = false
) where {E<:NTuple{2,Any}}
```

!!! note
    `binedges` 以外のすべてはオプションです（`binedges` から推測されます）。


# データ（および重みなど）を用いてヒストグラムを作成する

データのための位置引数と残りのためのキーワード引数を使用します：

```julia
FHist.Hist2D(array::E;
    counttype=Float64,
    binedges=nothing,
    weights=nothing,
    nbins=nothing,
    overflow=false)
) where {E<:NTuple{2,Any}}
```

!!! note
    データ（`array`）以外のすべてはオプションです（データから推測されます）。

