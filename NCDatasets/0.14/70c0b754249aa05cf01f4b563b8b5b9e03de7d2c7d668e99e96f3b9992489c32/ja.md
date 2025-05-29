```
a = nomissing(da,value)
```

配列 `da` の値を通常の Julia 配列 `a` として返し、すべての欠損値を `value`（型 `T` に変換）で置き換えます。この関数は `coalesce.(da,T(value))` と同じで、ここで T は `da` の要素型です。

## 例:

```julia-repl
julia> nomissing([missing,1.,2.],NaN)
# returns [NaN, 1.0, 2.0]
```
