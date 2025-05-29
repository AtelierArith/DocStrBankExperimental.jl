```
timeseriessimplices(time::AbstractVector; groupby::AbstractVector)
```

時間的に隣接する要素を接続するSimplexGraphを作成します。タイのケースでは、**すべての**ユニークな時間点にある要素が、**すべての**前の、現在の、次の時間点にある要素に接続されます。`groupby`が指定されている場合、要素は最初にグループごとに分けられ、その後時間によって接続されます。

# 例

```
julia> sg = timeseriessimplices([0.5, 1.0, 4.0]);

julia> sg.G
3×3 BitArray{2}:
 1  1  0
 1  1  1
 0  1  1

julia> sg = timeseriessimplices([0.5, 1.0, 1.0, 4.0]);

julia> sg.G
4×3 BitArray{2}:
 1  1  0
 1  1  1
 1  1  1
 0  1  1

julia> sg.w
3-element Array{Int64,1}:
 1
 2
 1

julia> sg = timeseriessimplices([2, 4, 6, 2, 4, 8]; groupby=["A","A","A","B","B","B"]);

julia> sg.G
6×6 BitArray{2}:
 1  1  0  0  0  0
 1  1  1  0  0  0
 0  1  1  0  0  0
 0  0  0  1  1  0
 0  0  0  1  1  1
 0  0  0  0  1  1
```
