```
Levels(col₁ => levels₁, col₂ => levels₂, ..., colₙ => levelsₙ; ordered=nothing)
```

列 `col₁`, `col₂`, ..., `colₙ` を指定されたレベル `levels₁`, `levels₂`, ..., `levelsₙ` を持つカテゴリカル配列に変換します。オプションで、どの列が `ordered` であるかを指定できます。

# 例

```julia
Levels(1 => 1:3, 2 => ["a", "b"], ordered=r"a")
Levels(:a => 1:3, :b => ["a", "b"], ordered=[:a])
Levels("a" => 1:3, "b" => ["a", "b"], ordered=["b"])
```
