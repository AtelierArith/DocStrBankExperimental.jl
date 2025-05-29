```
SequentialInterpolatedResampling{SequentialSamplingConstraint, InterpolationGrid}
```

は、最初に順次サンプリングを行い、その後サンプルを補間グリッドに補間することによって再サンプリングを行うべきであることを示します。

## フィールド

  * `sequential_constraint::SequentialSamplingConstraint`。順次サンプリング制約、例えば `StrictlyIncreasing()`。
  * `grid::InterpolationGrid`。再サンプリングされた描画（順次制約に従って生成された）を補間するグリッド、例えば `RegularGrid(0, 100, 2.5)`。

## 例

例えば、`SequentialInterpolatedResampling(StrictlyIncreasing(), RegularGrid(0:2:100))` は、順次描画を行い、その後グリッド 0:2:100 に補間されることを示します。
