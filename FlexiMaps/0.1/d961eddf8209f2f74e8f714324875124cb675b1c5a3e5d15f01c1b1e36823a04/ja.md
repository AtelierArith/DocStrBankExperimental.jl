```
flatmap_parent(f, A)
```

各 `f(a)` のすべての要素からなるコレクションを返します。これは `flatmap(f, A)` に似ています。

`A` の各要素は同じ親配列の `view` である必要があり、これらのビューは親のすべての要素をカバーする必要があります。結果の要素は、`a` の親配列の対応する要素と同じ順序になります。

# 例

```
julia> a = [10, 20, 30, 40, 50]

julia> avs = [view(a, [2, 5]), view(a, [3, 1, 4])]
2-element Vector{SubArray{Int64, 1, Vector{Int64}, Tuple{Vector{Int64}}, false}}:
 [20, 50]
 [30, 10, 40]

# 2倍して元の順序で再構成
julia> flatmap_parent(av -> 2 .* av, avs)
5-element Vector{Int64}:
  20
  40
  60
  80
 100
```
