```
neighborhood(point, tree, ntype)
neighborhood(point, tree, ntype, n::Int, w::Int = 1)
```

`point`の近傍を示すインデックスのベクトルを返します。`tree`は`tree = KDTree(data [, metric])`を使用して作成されます。`ntype`は近傍のタイプであり、[`AbstractNeighborhood`](@ref)の任意のサブタイプを指定できます。

`point`がデータに属する場合、すなわち`point = data[n]`の場合は2番目のメソッドを使用します。このとき、`w`はタイラーウィンドウ（正の整数）を表します。`abs(i - n) ≥ w`を満たすインデックスを持つ点のみが近傍として返され、近接する時間的隣接点を除外します。デフォルトの`w=1`は`point`自体を除外するケースです。

## 参考文献

`neighborhood`は、引数`ntype`を使用して、[NearestNeighbors.jl](https://github.com/KristofferC/NearestNeighbors.jl)の`NearestNeighbors.knn`および`inrange`関数を単純にインターフェースします。 ```
