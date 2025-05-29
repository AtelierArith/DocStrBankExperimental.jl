```
strip_adjacency(a)
```

隣接情報（すなわち、行列、グラフ、またはその他のデータ）を隣接オブジェクトから削除し、新しい隣接オブジェクトを構築するために `adjacency` 関数と併用できる `PartialAdjacency` を返す関数です。

# 例

```
julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A)
行列隣接, 3 obs

julia> Ac = adjacency(x->x,A)
計算可能な隣接

julia> Sm = strip_adjacency(Am)
部分隣接, 計算不可

julia> adjacency(Sm, A) # Sm は行列と共に使用する必要があります
行列隣接, 3 obs

julia> Sc = strip_adjacency(Ac)
部分隣接, 計算不可

julia> adjacency(Sc, A) # Sc は任意のデータと共に使用できます; f(A) を呼び出します、ここで f = x->x
行列隣接, 3 obs
```
