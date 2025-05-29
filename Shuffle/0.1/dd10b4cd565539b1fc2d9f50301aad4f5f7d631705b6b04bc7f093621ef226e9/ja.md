```
Faro{S}
Weave{S}
```

フィールドを持たないタイプで、`S` は `:in` の場合はインシャッフル、`:out` の場合はアウトシャッフルを表す[Faro (weave)](https://en.wikipedia.org/wiki/Faro_shuffle)カードシャッフルを表します。

シングルトンインスタンス [`infaro`](@ref)、[`outfaro`](@ref)、[`inweave`](@ref)、[`outweave`](@ref)を参照してください。

# 例

```jldoctest
julia> shuffle([1, 2, 3, 4, 5, 6, 7, 8], Faro{:out}())
8-element Array{Int64,1}:
 1
 5
 2
 6
 3
 7
 4
 8

julia> nshuffle(collect(1:52), 26, inweave) == collect(52:-1:1)
true
```
