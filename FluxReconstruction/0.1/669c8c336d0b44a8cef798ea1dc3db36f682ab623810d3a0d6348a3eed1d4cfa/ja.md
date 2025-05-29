```julia
positive_limiter(u, weights, ll, lr)
positive_limiter(u, weights, ll, lr, t0)

```

正の値を保持するためのスロープリミッター

*R. Vandenhoeck と A. Lani. 高速圧縮流のための暗黙的高次フラックス再構成ソルバー. Computer Physics Communications 242: 1-24, 2019."*

  * @arg u: 次元1の解点と次元2の状態を持つ保存変数
  * @arg γ: 比熱比
  * @arg weights: 平均値を計算するための数値重み
  * @arg ll&lr: 左/右エッジでのラグランジュ多項式
  * @arg t0=1.0: 最小制限スロープ
