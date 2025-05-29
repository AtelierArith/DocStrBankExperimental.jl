```
coef(r::AbstractDIDResult, name::String)
coef(r::AbstractDIDResult, name::Symbol)
coef(r::AbstractDIDResult, i::Int)
coef(r::AbstractDIDResult, inds)
```

名前（`coefnames`のように）または整数インデックスによるポイント推定値を取得します。名前または整数の反復可能なコレクションが指定された場合は、推定値のベクトルを返します。

名前によるインデックス指定には、メソッド [`coefinds(r)`](@ref) が必要です。さらに [`AbstractDIDResult`](@ref) も参照してください。
