```
assembly(model::OneDstructure, mesh::OneDMesh)
```

与えられたメッシュに対して1D構造のグローバル剛性行列と質量行列を計算します。

**入力**

  * `model`: OneDStructure

      * `Beam`: ビームモデル
      * `WaveEquation`: バー、ロッド、またはストリングモデル
  * `mesh`: OneDMesh

**出力**

  * `K`: グローバル剛性行列
  * `M`: グローバル質量行列
