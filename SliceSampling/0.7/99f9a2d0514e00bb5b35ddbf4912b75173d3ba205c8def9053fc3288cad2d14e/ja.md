```
LatentSlice(beta)
```

LiとWalkerによる潜在スライスサンプリングアルゴリズム[^LW2023]。

# 引数

  * `beta::Real`: 補助変数のガンマ分布のベータパラメータ。

# キーワード引数

  * `max_proposals::Int`: エラーを投げるまでに許可される最大提案数（デフォルト: `10000`）。
