```julia
stepifyedges(x::AbstractVector)
```

配列の最初と最後を除くすべての要素を重複させます。

`stepify` と組み合わせることで、ビンカウントとビンエッジのヒストグラムをステップ状の線として便利にプロットできます。

### 例

```julia
julia> stepifyedges([1,2,3,4])
6-element Vector{Int64}:
 1
 2
 2
 3
 3
 4

julia> plot(stepifyedges(binedges), stepify(bincounts))
# ヒストグラムのステップ状の線プロットを返します
```
