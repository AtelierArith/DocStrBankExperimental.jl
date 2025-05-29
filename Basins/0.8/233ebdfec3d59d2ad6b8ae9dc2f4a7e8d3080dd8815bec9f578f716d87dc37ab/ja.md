```
box_counting_dim(xg, yg, basin; kwargs...)
```

この関数は境界のボックスカウント次元を計算します。これは不確実性次元に関連しています。

[C. Grebogi, S. W. McDonald, E. Ott, J. A. Yorke, 最終状態の感度: 予測可能性への障害, Physics Letters A, 99, 9, 1983]

## 引数

  * `basin` : 流域の情報を含む行列。
  * `xg`, `yg` : テストする初期条件のグリッドを定義する1次元範囲ベクトル。

## キーワード引数

  * `kwargs...` これらの引数は `generalized_dim` に渡されます。ドキュメントについては `ChaosTools.jl` を参照してください。
