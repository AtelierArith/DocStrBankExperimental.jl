```
function optimize_by_sampling!(jump_model, sample_points; enhanced=true, exploitation_rate=0.67)
```

サンプルポイントで「局所」最適化問題を反復的に解くことによってニューラルネットワークを最適化します。最良の（最適、極値）解が返されます。

# 引数

  * `jump_model`: 定式化（および目的関数）を含む `JuMP` モデル
  * `sample_points`: 列がサンプル入力である行列。

# オプション引数

  * `enhanced`: 局所最適解を探索するか、局所ハイパープレーンのコーナーのみを探索するかを制御します。
  * `exploitation_rate`: アルゴリズムが局所探索を行う頻度と新しいポイントをサンプリングする頻度を制御します。
