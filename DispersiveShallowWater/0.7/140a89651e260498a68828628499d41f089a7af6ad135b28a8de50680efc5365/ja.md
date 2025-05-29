```
initial_condition_dingemans(x, t, equations::AbstractShallowWaterEquations, mesh)
```

ディンゲマンズの実験で行われるように、波発生器によって生成される波を近似するためにオイラー方程式の分散関係を使用する初期条件です。地形は台形です。`equations.eta0 = 0.8`であると仮定されています。

参考文献:

  * Magnus Svärd, Henrik Kalisch (2023) 新しいエネルギー制約付きボッシネスクモデルと良好にバランスの取れた安定した数値離散化 [arXiv: 2302.09924](https://arxiv.org/abs/2302.09924)
  * Maarten W. Dingemans (1994) ボッシネスク様モデルと実験室測定との計算の比較 [link](https://repository.tudelft.nl/islandora/object/uuid:c2091d53-f455-48af-a84b-ac86680455e9/datastream/OBJ/download)
