```
Rename(:col₁ => :newcol₁, :col₂ => :newcol₂, ..., :colₙ => :newcolₙ)
Rename([:col₁ => :newcol₁, :col₂ => :newcol₂, ..., :colₙ => :newcolₙ])
```

Renames the columns `col₁`, `col₂`, ..., `colₙ` to `newcol₁`, `newcol₂`, ..., `newcolₙ`.

```
Rename(fun)
```

Renames the table columns using the modification function `fun` that takes a  string as input and returns another string with the new name.

# Examples

```julia
Rename(1 => :x, 3 => :y)
Rename(:a => :x, :c => :y)
Rename("a" => "x", "c" => "y")
Rename([1 => "x", 3 => "y"])
Rename([:a => "x", :c => "y"])
Rename(["a", "c"] .=> [:x, :y])
Rename(nm -> nm * "_suffix")
```
