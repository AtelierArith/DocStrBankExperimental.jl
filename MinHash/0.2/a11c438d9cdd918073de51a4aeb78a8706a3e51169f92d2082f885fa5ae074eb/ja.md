```
intersectionlength(y::MinHashSketch, y::MinHashSketch)
```

`x` と `y` の両方に含まれるハッシュの数を、通常の集合操作を使用するよりも効果的にカウントします。

# 例

```julia-repl
julia> x = sketch(1:10000, 100); y = sketch(5000:15000, 100);

julia> intersectionlength(x, y)
49
```
