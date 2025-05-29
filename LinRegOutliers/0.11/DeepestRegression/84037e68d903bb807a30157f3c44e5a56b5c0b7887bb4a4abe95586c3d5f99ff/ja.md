```
deepestregression(setting; maxit = 1000)
```

ディープレスト回帰パラメータを推定します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `maxit`: 最大反復回数

# 説明

ディープレスト回帰推定量の係数を推定します。

# 参考文献

Van Aelst S., Rousseeuw P.J., Hubert M., Struyf A. (2002). The deepest regression method. Journal of Multivariate Analysis, 81, 138-166.

# 出力

  * `betas`: 推定された回帰係数のベクトル。
