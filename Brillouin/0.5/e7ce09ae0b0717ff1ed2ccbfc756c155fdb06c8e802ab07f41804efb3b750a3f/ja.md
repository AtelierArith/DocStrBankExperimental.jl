```
setting(x::Union{KPath, KPathInterpolant, Cell})
```

`x`の座標の基底設定を返します。返される値は、メンバー値が`LATTICE`（すなわち、格子ベクトルの基底における座標）または`CARTESIAN`（すなわち、直交基底における座標）である[`BasisEnum`](@ref) 列挙型のメンバーです。デフォルトでは、Brillouinのメソッドは`LATTICE`設定の座標を返します。
