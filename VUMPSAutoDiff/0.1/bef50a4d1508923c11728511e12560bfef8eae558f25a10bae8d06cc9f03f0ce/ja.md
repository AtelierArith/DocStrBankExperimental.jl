```
VOMPSOptions
```

VOMPSアルゴリズムの設定構造体。

# フィールド

  * `tol::Float64`: VOMPS更新の収束許容誤差
  * `maxiter::Int`: 最大反復回数
  * `verbosity::Int`: 出力の冗長性レベル (0 = サイレント, 1 = 基本, 2 = 詳細)
  * `do_gauge_fixing::Bool`: 収束後のゲージ固定を有効/無効にする
