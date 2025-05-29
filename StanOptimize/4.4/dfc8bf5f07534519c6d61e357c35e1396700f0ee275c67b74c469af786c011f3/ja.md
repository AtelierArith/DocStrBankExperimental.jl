`stan_optimize(...)`

StanJuliaのOptimizationModel <: CmdStanModelを最適化します

# 拡張ヘルプ

### ディスパッチ引数

```julia
* `m:: OptimizeModel`             # CmdStanModelのサブタイプ
* `use_json=true`                 # データおよび初期化ファイルにJSON3を使用
```

### キーワード引数

```julia
* `init`                               : 初期化辞書
* `data`                               : データ辞書
```

```julia
stan_run(m; ...)
stan_run(m, use_json; kwargs...)

```

### 戻り値

```julia
* `rc`                                 # 戻りコード、0は成功を示す。
```

他のキーワード引数については拡張ヘルプを参照してください（ `??stan_optimize` ）。

# 拡張ヘルプ

### 追加の設定キーワード引数

```julia
* `num_chains=4`                       # チェーンの数を更新。
* `num_threads=8`                      # スレッドの数を更新。

* `seed=-1`                            # シード値を設定。
* `init_bound=2`                       # 初期化の境界
* `refresh=200`                        # 出力にストリーム

* `algorithm=:lbfgs`                   # アルゴリズム: :lbfgs, bfgs または :newton。
* `init_alpha=0.0001`                  # 最初の反復のラインサーチステップサイズ。
* `tol_obj=9.999e-13`                  # 収束許容値
* `tol_rel_obj=9.999e-13`              # 相対収束許容値
* `tol_grad=9.999e-13`                 # 勾配のノルムに関する収束許容値
* `tol_rel_grad=9.999e-13`             # 相対収束許容値
* `tol_param=1e-8`                     # パラメータの変化に関する収束許容値

* `history_size=`                      # L-BFGSのために保持する履歴の量

* `iter=200`                           # ニュートン反復の総数
* `save_iterations=0`                  # 出力に反復をストリーム
```
