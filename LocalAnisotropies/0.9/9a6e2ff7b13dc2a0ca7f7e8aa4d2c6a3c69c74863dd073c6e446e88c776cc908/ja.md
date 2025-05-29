```
to_vtk(vtkfile, coords, localaniso; dir=:ellips, magnitude=:ranges)
```

ローカル異方性 `localaniso` を `coords` で VTK 形式にエクスポートします。デフォルトではローカル楕円体がエクスポートされます。`dir` が `:X`、`:Y`、`:Z` または `:XYZ` に設定されている場合、ローカルベクトル/矢印がこれらの軸にエクスポートされます。大きさは `:ranges`（デフォルト）または `:ratios` として表現できます。`:ratios` の場合、`ratio1=range2/range1` および `ratio2=range3/range1` となります。座標の配列の代わりに、`coords` は地理参照された空間オブジェクトだけでも構いません。出力される `.vtu` ファイルは Paraview や類似のソフトウェアで読み込むことができ、方向をプロットするために Glyphs として処理されます。`dir = :ellips` の場合、適切な視覚化のために TensorGlyphs を使用する必要があります（固有値の抽出を無効にする必要があります）。
