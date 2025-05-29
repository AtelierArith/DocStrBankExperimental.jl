```
NonlinearObservationModel(h::Function,V::Symmetric)
NonlinearObservationModel(h::Function,V::AbstractMatrix)
```

測定関数 h と対称ゼロ平均測定ノイズを持つ非線形観測動力学モデルを対称共分散行列 V で構築します。
