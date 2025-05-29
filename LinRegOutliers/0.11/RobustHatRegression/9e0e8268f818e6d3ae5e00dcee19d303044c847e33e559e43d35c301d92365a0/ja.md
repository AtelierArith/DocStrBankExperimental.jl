```
robhatreg(X, y)
```

ロバストハット行列法を使用してロバスト回帰を実行します。

# 引数

  * `X::AbstractMatrix`: 設計行列。
  * `y::AbstractVector`: 応答ベクトル。

# 戻り値

  * 次の内容を含む辞書
  * `betas::AbstractVector`: 推定された係数。

# 参考文献

Satman, Mehmet Hakan, 線形回帰における外れ値検出アルゴリズムのためのロバストな初期基本部分集合選択法, In Press
