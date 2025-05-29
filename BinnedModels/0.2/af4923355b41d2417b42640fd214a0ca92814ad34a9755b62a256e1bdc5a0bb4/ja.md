```
fit_binedges(data::AbstractVector{<:Real})::BinEdges
fit_binedges(data::NTuple{N,AbstractVector{<:Real}})::NTuple{N,BinEdges}
```

`data` に対して適切なビンエッジを返します。`algorithm` を使用します。

`data` は実数値のベクトル、または多次元データのための実数値のベクトルのタプルである可能性があります。
