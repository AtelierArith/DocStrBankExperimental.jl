stan_variational()

StanJuliaのVariationalModel (<: CmdStanModel) からサンプルを取得します。

## 必要な引数

```julia
* `m::VariationalModel`                # VariationalModel.
* `use_json=true`                      # データと初期値ファイルにJSON3を使用
```

### 最も頻繁に使用されるキーワード引数

```julia
* `data`                               # 観測値のDictまたはNamedTuple。
* `init`                               # 初期値のDictまたはNT（デフォルト：-2から+2）。
```

### 戻り値

```julia
* `rc`                                 # 戻りコード、0は成功。
```

他のキーワード引数についての詳細なヘルプは、（ `??stan_sample` ）を参照してください。

# 拡張ヘルプ

### 追加の設定キーワード引数

```julia
* `num_chains=4`                       # チェーンの数を更新。
* `num_threads=8`                      # スレッドの数を更新。

* `seed=-1`                            # シード値を設定。
* `refresh=100`                        # 出力へのストリーム。
* `init_bound=2`                       # 初期値の境界。

* `algorithm=:meanfield`               # :meanfield または :fullrank
* `iter=10000`                         # ADVIイテレーションの最大数
* `grad_samples=1`                     # 勾配を計算するためのサンプル数
* `elbo_samples=100`                   # ELBO推定のためのサンプル数
* `eta=1.0`                            # ステップサイズスケーリングパラメータ

* `engaged=true`                       # Eta適応がアクティブ
* `adapt_iter=50`                      # eta適応のためのイテレーション数

* `tol_rel_obj=0.01`                   # 収束のための許容誤差
* `eval_elbo=100`                      # ELBO評価の間のイテレーション数
* `output_samples=1000`                # 保存する後方サンプルの近似数
```
