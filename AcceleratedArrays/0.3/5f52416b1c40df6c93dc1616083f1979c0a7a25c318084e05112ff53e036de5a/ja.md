```
greaterthan(x)
```

`x` よりも即座に大きい値を返します。その値はほぼ `x` と等しいですが、`x` と `greaterthan(x)` の間に他の値（どのタイプでも）は存在しないべきです。これは、Julia の `isless` および `isequal` の標準的な全順序に従います。

他の用途の中で、これは開始点を除外する `Interval` を作成するために使用されることがあります。

`lessthan` も参照してください。

# 例

```julua
julia> isequal(10, greaterthan(10))
false

julia> isless(10, greaterthan(10))
true

julia> 0 ∈ 0..10
true

julia> 0 ∈ greaterthan(0)..10
false
```
