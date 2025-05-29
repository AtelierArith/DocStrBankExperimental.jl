```
EarthConfig(; constraints=Set{Vector{Bool}}(), num_knots=20, maxit=10, maxorder=2, maxdegree=2,
            knot_penalty=ifelse(maxorder>1, 3, 2), min_r2=0.001, min_coef=0.01,
            prune::Bool=true, refit::Symbol=:lasso)
```

# キーワード引数

  * `num_knots`: 各変数のためのヒンジ関数のノットの数。
  * `maxit`: 基底構築の反復回数。
  * `constraints`: 用語を生成するために使用できる変数の組み合わせを制約するビットベクトルのセット。
  * `prune`: false の場合、基底構築ステップを実行しますが、剪定ステップは実行しません。
  * `maxorder`: 単一の用語に存在できる異なる変数の最大数。
  * `maxdegree`: 単一の変数において1つの用語に現れることができるヒンジの最大数。
  * `knot_penalty`: 新しい用語がモデルに入ることができる容易さを制御するパラメータ。
  * `min_r2`: R2の増加がこの値を下回る場合、前方パスを終了します。
  * `min_coef`: 標準化された係数がこの値を下回る用語は剪定されます。
  * `prune`: true の場合、Lassoを使用してモデルを剪定します。
  * `refit`: 剪定後、Lasso (:lasso) または OLS (:ols) を使用してモデルを再フィットします。
