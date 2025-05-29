```
combinedims(array_of_arrays)
```

ネストされた配列構造の次元を新しいフラットな配列に結合します。

これは `splitdims` / `splitdimsview` の逆操作です。

この関数の遅延バージョンである `combinedimsview` も参照してください。

# 例

```julia
julia> combinedims([[1, 2], [3, 4]])
2×2 Array{Int64,2}:
 1  3
 2  4
```
