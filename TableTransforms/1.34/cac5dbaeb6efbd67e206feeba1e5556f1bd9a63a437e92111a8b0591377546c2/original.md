```
Levels(col₁ => levels₁, col₂ => levels₂, ..., colₙ => levelsₙ; ordered=nothing)
```

Convert columns `col₁`, `col₂`, ..., `colₙ` to categorical arrays with given levels `levels₁`, `levels₂`, ..., `levelsₙ`. Optionally, specify which columns are `ordered`.

# Examples

```julia
Levels(1 => 1:3, 2 => ["a", "b"], ordered=r"a")
Levels(:a => 1:3, :b => ["a", "b"], ordered=[:a])
Levels("a" => 1:3, "b" => ["a", "b"], ordered=["b"])
```
