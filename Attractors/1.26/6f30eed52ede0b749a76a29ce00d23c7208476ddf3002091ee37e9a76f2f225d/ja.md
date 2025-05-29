```
basins_of_attraction(mapper::AttractorMapper, grid::Tuple) → basins, attractors
```

与えられた `mapper` によって特定された全ての引力盆地を計算し、（おそらく近似された）見つかった引力子と共に返します。

`grid` は、初期条件のグリッドを定義する範囲のタプルであり、状態空間を各範囲のステップサイズのボックスに分割します。例えば、`grid = (xg, yg)` で、`xg = yg = range(-5, 5; length = 100)` の場合です。グリッドは、`mapper` で使用される積分器/システムが期待する状態空間と同じ次元でなければなりません。例えば、[`ProjectedDynamicalSystem`](@ref) は低次元の射影に使用できます。この特別なケースでは、`plane` が `Tuple{Int, <: Real}` である [`PoincareMap`](@ref) があります。この特別なシナリオでは、グリッドは状態空間よりも1次元小さくすることができ、その場合、分割はポアンカレ写像が作用する超平面上で直接行われます。

`basins_of_attraction` 関数は、[`basins_fractions`](@ref) によって返される `labels` を使用し、それらを `grid` によって示される状態空間の分割に対応する完全な配列に単純に割り当てる便利な5行のコードラッパーです。

さらに、[`convergence_and_basins_of_attraction`](@ref) も参照してください。
