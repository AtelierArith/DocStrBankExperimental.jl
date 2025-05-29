```
init_mom!(m::WSVarLmmModel, solver; init = init_ls!(m), parallel = false)
```

`VarLmmModel`オブジェクトの`τ`と`Lγ`をモーメント法（MoM）を用いて`m.obs[i].res`の残差を使って初期化します。これは重みのないNLS問題を解くことを含みます。

# 位置引数

  * `m`: `WSVarLmmModel`オブジェクト。
  * `solver`: NLPソルバー。デフォルトは`IpoptSolver(print_level=0, mehrotra_algorithm="yes", warm_start_init_point="yes", max_iter=100)`です。

# キーワード引数

  * `init`: NLS問題の初期化子。デフォルトは`init_ls!(m)`です。`init=m`の場合、

その場合、`m.τ`と`m.Lγ`に提供された値を出発点として使用します。  

  * `parallel::Bool`: マルチスレッド。デフォルトは`false`です。
