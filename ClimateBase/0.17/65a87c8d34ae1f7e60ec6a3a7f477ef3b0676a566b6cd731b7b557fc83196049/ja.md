```
interpolate_height2pressure(A::ClimArray, pressure_levels::Vector; extrapolation_bc=NaN )
```

垂直座標が圧力の `ClimArray` を返します。圧力レベルは、静水圧平衡に基づいて `height2pressure` 関数を使用して計算され、その後指定されたレベルに補間されます。

`A`: 地上からの高さ [m] を高さ座標とする `ClimArray`。 `pressure_levels`: `A` が補間されるべきパスカル単位の圧力レベルを含むベクター。 `extrapolation_bc`: 外挿はデフォルトで `NaN` に設定されていますが、任意の値または `extrapolation_bc = Line()` を使用した線形外挿にすることができます。他の外挿方法については `Interpolations` パッケージを使用してください。
