```
body_forces_history(system, surface_history, property_history; frame=Body())
```

`property_history`の各時間ステップでの剛体力係数`CF`、`CM`を返します。

# 引数:

  * `system`: システムプロパティを保持する[`System`](@ref)型のオブジェクト
  * `surface_history`: 各時間ステップでの表面のベクトルで、各表面は（[`SurfacePanel`](@ref）を参照）形状が(nc, ns)の表面パネルの行列で表されます。ここで`nc`は弦方向パネルの数、`ns`は翼幅方向パネルの数です。
  * `property_history`: 各時間ステップでの各表面の表面プロパティのベクトルで、表面プロパティは（[`PanelProperties`](@ref）を参照）形状が(nc, ns)のパネルプロパティの行列で表されます。ここで`nc`は弦方向パネルの数、`ns`は翼幅方向パネルの数です。

# キーワード引数

  * `frame`: `CF`と`CM`を返すフレーム。オプションは[`Body()`](@ref)（デフォルト）、[`Stability()`](@ref)、および[`Wind()`](@ref)です。
