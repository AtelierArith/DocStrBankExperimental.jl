```
gradview(sess::PyObject, pl::PyObject, loss::PyObject, u0; scale::Float64 = 1.0)
```

自動微分と有限差分収束を視覚化します。正しく実装された微分可能なコードの場合、ADの収束率は2で、FDの収束率は1であるべきです（定常点で評価されていない場合）。

  * `scale`: 摂動のステップサイズを制御できます。
