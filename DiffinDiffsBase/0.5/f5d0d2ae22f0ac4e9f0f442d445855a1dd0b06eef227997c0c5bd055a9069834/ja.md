```
vcov(r::AbstractDIDResult, name1::Union{String, Symbol}, name2::Union{String, Symbol}=name1)
vcov(r::AbstractDIDResult, i::Int, j::Int=i)
vcov(r::AbstractDIDResult, inds)
```

名前（`coefnames`のように）または整数インデックスによって2つの係数間の共分散を取得します。名前またはインデックスが1つだけ指定された場合は分散を返します。名前または整数の選択された係数のイテラブルコレクションが指定された場合は、分散共分散行列を返します。

名前によるインデックス指定にはメソッド [`coefinds(r)`](@ref) が必要です。さらに [`AbstractDIDResult`](@ref) も参照してください。
