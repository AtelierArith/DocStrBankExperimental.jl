```
write_vtk(name, surface_history, property_history, wake_history; kwargs...)
```

非定常シミュレーションジオメトリを視覚化のためにParaviewファイルに書き込みます。

# 引数

  * `name`: 生成されるファイルの基本名
  * `surface_history`: 各時間ステップでの表面のベクトルで、各表面は表面パネルの行列（形状は（nc, ns）で、`nc`は弦方向のパネル数、`ns`はスパン方向のパネル数）で表されます（[`SurfacePanel`](@ref)を参照）。
  * `property_history`: 各時間ステップでの各表面の表面特性のベクトルで、表面特性はパネル特性の行列（形状は（nc, ns）で、`nc`は弦方向のパネル数、`ns`はスパン方向のパネル数）で表されます（[`PanelProperties`](@ref)を参照）。
  * `wake_history`: 各時間ステップでの各表面に対応するウェイクのベクトルで、各ウェイクはウェイクパネルの行列（形状は（nw, ns）で、`nw`は弦方向のウェイクパネル数、`ns`はスパン方向のパネル数）で表されます（[`WakePanel`](@ref)を参照）。
  * `dt`: 時間ステップのベクトル

# キーワード引数:

  * `symmetric`: （`properties`が提供されている場合は必須）各表面の誘導速度を計算する際に鏡像（X-Z平面に対して）が使用されたかどうかを示すフラグ。
  * `wake_length`: 後流渦を延長する距離。デフォルトは10
  * `metadata`: 生成されるファイルに含めるメタデータの辞書
