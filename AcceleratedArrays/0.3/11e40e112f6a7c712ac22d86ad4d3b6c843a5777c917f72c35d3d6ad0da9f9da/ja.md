```
lessthan(x)
```

`x` よりも即座に小さい値を返します。その値は `x` にほぼ等しいですが、完全には等しくありません - `x` と `lessthan(x)` の間に他の値（どのタイプでも）が存在してはいけません。これは Julia の `isless` と `isequal` の標準的な全順序に従います。

他の用途の中で、これは端点を除外する `Interval` を作成するために使用されることがあります。

`greaterthan` も参照してください。

# 例

```julua
julia> isequal(lessthan(10), 10)
false

julia> isless(lessthan(10), 10)
true

julia> 10 ∈ 0..10
true

julia> 10 ∈ 0..lessthan(10)
false
```
