```
CategorySpace(categories)
```

提供されたカテゴリ（`Vector`）によって定義された検索空間を定義します。

# 例

```julia-repl
julia> space = CategorySpace([:soft, :medium, :high]);

julia> rand(space)
:soft

julia> cardinality(space)
3
```
