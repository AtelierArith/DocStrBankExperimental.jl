```
sequentialise(data)
```

配列の配列を最初の次元を通じて連結された配列に変換します。

これは、Transducersから得られたデータを使用して図をプロットする際に便利です。

# 例

```jldoctest
julia> using LazyFym

julia> sequentialise([[1, 2], [3, 4], [5, 6]])
3×2 Array{Int64,2}:
 1  2
 3  4
 5  6
```
