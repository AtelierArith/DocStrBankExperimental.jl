```
struct PqPoints <: AbstractPqCurve
PqPoints(power_levels::Vector{Real}, discharge_levels::Vector{Real})
PqPoints(eq::Real)
```

水の放出/ポンピングと発電/消費の関係は、一連の放出および電力値（PQポイント）によって表されます。

## フィールド

  * **`power_levels::Vector{Real}`** は電力値のベクトルです。
  * **`discharge_levels::Vector{Real}`** は放出値のベクトルです。

2つのベクトルは同じサイズでなければならず、電力と放出値がエネルギー（水に蓄えられた）から電気（電力）への変換、または電気エネルギーから貯水池に水として蓄えられるエネルギーへの変換を説明するように順序付けられている必要があります [`HydroGenerator`](@ref) ノードまたは [`HydroPump`](@ref) ノードのために。

各ベクトルの最初の値はゼロであるべきです。さらに、ベクトルは設置された容量に対して相対的である必要があり、したがって電力ベクトルまたは放出ベクトルのいずれかが範囲 [0, 1] にある必要があります。

単一の `Real` が入力として提供されると、エネルギー等価入力を通じて2つの配列が構築されます。このアプローチが使用される場合、ノードの設置容量は [`HydroGenerator`](@ref) または [`HydroPump`](@ref) ノードの電力容量を参照する必要があります。

!!! note
    説明された電力-放出関係は、[`HydroGenerator`](@ref) ノードに対しては凹であり、[`HydroPump`](@ref) ノードに対しては凸であるべきです。


```
