`robinson_schensted(p::AbstractVector{<:Integer})`

は、ロビンソン-シェンステッド対応によって置換 `p` に関連付けられた標準タブローのペアを返します。

```julia-repl
julia> robinson_schensted([2,3,4,1])
([[1, 3, 4], [2]], [[1, 2, 3], [4]])
```
