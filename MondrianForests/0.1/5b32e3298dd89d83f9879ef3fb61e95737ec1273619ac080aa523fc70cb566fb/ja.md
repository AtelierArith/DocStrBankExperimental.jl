```
get_common_refinement(trees::Vector{MondrianTree{d}}) where {d}
```

複数のモンドリアンツリーの共通の細分化を取得します。葉セルは `trees` 内のすべての葉セルの交差点です。分割時間を保持し、新しい同等の `MondrianTree` を返します。

# 例

```julia
trees = [MondrianTree(2, 3.0) for _ in 1:3]
refined_tree = get_common_refinement(trees)
```
