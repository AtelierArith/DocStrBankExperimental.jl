```julia
generate_ci_problem(
    shooting,
    prob_bif,
    prob_de,
    sol,
    tspan;
    prob_mono,
    alg,
    alg_mono,
    use_bordered_array,
    ksh...
)

```

解の周期軌道問題を生成します。

## 引数

  * `pb` 基本情報を提供する `ShootingProblem`、例えば時間スライスの数 `M`
  * `bifprob` ベクトル場を提供するための分岐問題
  * `prob_de::ODEProblem` `sol` に関連する
  * `sol` 基本的に `ODEProblem` または関数 `t -> sol(t)`
  * `tspan::Tuple` 周期軌道の周期の推定
  * `alg` コーシー問題を解くためのアルゴリズム
  * `prob_mono` モノドロミーの問題
  * `alg_mono` モノドロミーコーシー問題を解くためのアルゴリズム
  * `k` `ShootingProblem` のコンストラクタに渡されるキーワード引数

## 出力

  * `ShootingProblem` と初期推定を返します。
