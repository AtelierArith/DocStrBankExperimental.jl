```julia
stepify(x::AbstractVector)
```

配列の各要素を重複させます。

`stepifyedges` と組み合わせることで、ビンカウントとビンエッジのヒストグラムをステップ状の線として便利にプロットできます。

### 例

```julia
julia> stepify([1,3,2])
6-element Vector{Int64}:
 1
 1
 3
 3
 2
 2

julia> plot(stepifyedges(binedges), stepify(bincounts))
# ヒストグラムのステップ状の線プロットを返します
```
