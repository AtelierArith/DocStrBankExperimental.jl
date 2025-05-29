```
invert(a)
```

入れ子のコンテナ `a` の順序を逆にして新しい入れ子のコンテナを返します。例えば、配列の辞書を辞書の配列に変換し、`a[i][j] === invert(a)[j][i]` となるようにします。

内側と外側の構造のキーを知るためには、入力コンテナ `a` は空であってはいけません。

# 例

```julia
julia> invert([[1,2,3],[4,5,6]])
3-element Array{Array{Int64,1},1}:
 [1, 4]
 [2, 5]
 [3, 6]

julia> invert((a = [1, 2, 3], b = [2.0, 4.0, 6.0]))
3-element Array{NamedTuple{(:a, :b),Tuple{Int64,Float64}},1}:
 (a = 1, b = 2.0)
 (a = 2, b = 4.0)
 (a = 3, b = 6.0)
```
