```julia
stan_run(m; ...)
stan_run(m, use_json; kwargs...)

```

StanJulia PathfinderModel (<: CmdStanModel) のサンプル。

## 必要な引数

```julia
* `m::PathfinderModel`                 # PathfinderModel.
* `use_json=true`                      # データファイルにJSON3を使用
```

追加のキーワード引数のリストについては `??stan_pathfinder` を使用してください。

### 戻り値

```julia
* `rc`                                 # 戻り値コード、0は成功。
```

他のキーワード引数についての詳細なヘルプは ( `??stan_sample` ) を参照してください。

# 拡張ヘルプ

### 追加の設定キーワード引数

```julia
* `num_chains=4` # チェーンの数。

* `init=2` # 初期値の境界。
* `seed=rand(primes(1, 20000001), num_chains)` # シード値の配列。
* `refresh=100` # 出力ストリーム。
* `sig_figs=-1` # 使用される有効数字の数。
* `num_threads=1` # スレッドの数。

* `init_alpha=0.001`
* `tol_obj=9.99999999e-13`
* `tol_rel_obj=1000`
* `tol_grad=1e-8`
* `tol_rel_grad=10000000`
* `tol_param=1e-4`

* `history_size=5`
* `num_psis_draws=1000`
* `num_paths=4`

* `psis_resample=true`
* `calculate_lp=true`
* `save_single_paths=false`
* `save_cmdstan_config=true`

* `max_lbfgs_iters=1000`
* `num_draws=1000`
* `num_elbo_draws=25`
```
