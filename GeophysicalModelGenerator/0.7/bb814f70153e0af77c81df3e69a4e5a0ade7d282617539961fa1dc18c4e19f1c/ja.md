```
add_fault!(Phase, Temp, Grid::AbstractGeneralGrid;
    Start=(20,100), End=(10,80),
    Fault_thickness=10.0,
    Depth_extent=nothing,
    DipAngle=0e0,
    phase=ConstantPhase(1),
    T=nothing,
    cell=false)
```

指定された3Dグリッドに対して、`Phase`および`Temp`配列を変更することで断層を追加します。2Dグリッドの場合は、代わりに`add_box`を使用してください。

# 引数

  * `Phase`: フェーズ配列
  * `Temp`: 温度配列
  * `Grid`: 断層を追加するグリッド。
  * `Start`: 断層の開始座標を表すタプル (X, Y)。
  * `End`: 断層の終了座標を表すタプル (X, Y)。
  * `Fault_thickness`: 断層の厚さ。
  * `Depth_extent`: 断層の深さの範囲。`nothing`の場合、断層は全領域を通過します。
  * `DipAngle`: 断層の傾斜角。
  * `phase`: 断層に割り当てるフェーズ。
  * `T`: 断層に割り当てる温度。`nothing`の場合、温度は変更されません。

# 例

```julia
add_fault!(Phase, Temp, Grid;
        Start=(20,100), End=(10,80),
        Fault_thickness=10.0,
        Depth_extent=(-25.0, 0.0),
        DipAngle=-10.0,
        phase=ConstantPhase(1)
        )
```
