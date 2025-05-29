```
Rename(:col₁ => :newcol₁, :col₂ => :newcol₂, ..., :colₙ => :newcolₙ)
Rename([:col₁ => :newcol₁, :col₂ => :newcol₂, ..., :colₙ => :newcolₙ])
```

列 `col₁`、`col₂`、...、`colₙ` を `newcol₁`、`newcol₂`、...、`newcolₙ` に名前変更します。

```
Rename(fun)
```

文字列を入力として受け取り、新しい名前の文字列を返す修正関数 `fun` を使用してテーブルの列名を変更します。

# 例

```julia
Rename(1 => :x, 3 => :y)
Rename(:a => :x, :c => :y)
Rename("a" => "x", "c" => "y")
Rename([1 => "x", 3 => "y"])
Rename([:a => "x", :c => "y"])
Rename(["a", "c"] .=> [:x, :y])
Rename(nm -> nm * "_suffix")
```
