```
VT_mechanical_stability(model,V,T,z = SA[1.0])::Bool
```

(V,T,z) ペアの機械的安定性を実行し、`true/false` を返します。等温圧縮率が負でないかをチェックします。

!!! note
    この関数には `p`,`T` の対応するものはありません。なぜなら、`volume(model,p,T,z)` を通じて体積を計算すると、それは定義上、機械的に安定した相になるからです。

