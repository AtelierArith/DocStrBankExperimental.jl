```
PointValues(cv::CellValues)
PointValues([::Type{T}], func_interpol::Interpolation, [geom_interpol::Interpolation])
```

`CellValues`と似ていますが、単一の更新可能な「数値点」を持っています。`PointValues`は、[`PointEvalHandler`](@ref)と共に、領域の任意の点での関数/勾配の評価に使用されます。

`PointValues`は`CellValues`から、または補間から直接作成できます。

`PointValues`は他の`CellValues`と同様に再初期化されますが、「数値点」のローカル参照座標が変わるため、要素座標に加えて[`reinit!`](@ref)に渡す必要があります: `reinit!(pv, coords, local_coord)`。あるいは、[`PointIterator`](@ref)を使用して`PointEvalHandler`を反復処理する際に、[`PointLocation`](@ref)で再初期化することもできます。

関数/勾配の評価において、`PointValues`は`CellValues`と同様に使用されます。すなわち、[`function_value`](@ref)、[`function_gradient`](@ref)などを使用しますが、数値点インデックスを指定する必要はありません（`PointValues`は1つしか持たないため、これがデフォルトです）。
