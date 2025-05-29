```
ParticleMeshCoupling1D( mesh, no_particles, spline_degree, 
                      smoothing_type )
```

カーネルスムーザーは、均一メッシュ上に配置された任意の次数のスプラインを使用します。インデックス i のスプラインは、点 i から始まります。

  * `delta_x` : 両方向のグリッド間隔の値。
  * `n_grid` : 各方向に沿ったポイントの数を含む配列
  * `no_particles` : 基本的な PIC メソッドの粒子の数
  * `spline_degree` : スムージングカーネルスプラインの次数
  * `n_span` : スプラインがゼロでない区間の数 (spline_degree + 1)
  * `scaling` : :galerkin または :collocation に依存するスケーリングファクター
  * `n_quad_points` : 数値積分点の数
  * `spline_val`: スプライン評価のためのスクラッチデータ
  * `spline_val_more` : スプライン評価のための追加のスクラッチデータ
  * `quad_x, quad_w` : 数値積分の重みと点

!!! note
    現在は 1D バージョンのみが実装されています。

