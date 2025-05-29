```julia
generate_ci_problem(
    pb,
    bifprob,
    prob_de,
    sol,
    tspan;
    alg,
    ksh...
)

```

解の周期軌道問題を生成します。

## 引数

  * `pb` 基本情報を提供する `PoincareShootingProblem`、例えば時間スライスの数 `M`
  * `bifprob` ベクトル場を提供するための分岐問題
  * `prob_de::ODEProblem` `sol` に関連する
  * `sol` 基本的に、そして `ODEProblem`
  * `period` 周期軌道の周期の推定
  * `k` `ShootingProblem` のコンストラクタに渡されるキーワード引数

## 出力

  * `ShootingProblem` と初期推定を返します。
