```
interpolate_pressure2height(A::ClimArray,heights::Vector; extrapolation_bc=NaN)
```

地上の高さを基準とした垂直座標を持つ `ClimArray` を返します。地上の高さは、静水圧平衡に基づいて `pressure2height` 関数を使用して計算され、その後、指定された高さに補間されます。

`A`: 高さ座標として圧力 [Pa] を持つ ClimArray。 `heights`: `A` が地上のメートル単位で補間されるべき高さを含むベクトル。 `extrapolation_bc`: 補外はデフォルトで `NaN` に設定されていますが、任意の値または `extrapolation_bc = Line()` を使用した線形補外にすることができます。他の補外方法については、`Interpolations` パッケージを使用してください。
