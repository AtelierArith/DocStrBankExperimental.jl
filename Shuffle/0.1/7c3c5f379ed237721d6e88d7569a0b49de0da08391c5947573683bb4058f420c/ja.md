```
GilbertShannonReeds
```

フィールドを持たない型で、[Gilbert-Shannon-Reeds](https://en.wikipedia.org/wiki/Gilbert–Shannon–Reeds_model) モデルのカードシャッフルを表します。シングルトンインスタンス [`gsrshuffle`](@ref) を参照してください。

このアルゴリズムにはインプレース [`shuffle!`](@ref) は実装されていません。ただし、インプレース [`nshuffle!`](@ref) は実装されています。

# 例

```jldoctest
julia> mt = MersenneTwister(1234);

julia> shuffle(mt, 1:7, gsrshuffle)
7-element Array{Int64,1}:
 5
 6
 1
 2
 7
 3
 4

```
