stan_sample()

StanJulia SampleModel (<: CmdStanModel.) からサンプリングします。

## 必要な引数

```julia
* `m <: CmdStanModels`                 # SampleModel.
* `use_json=true`                      # データと初期化ファイルに JSON3 を使用
* `check_num_chains=true`              # 正しい Julia チェーンと C++ チェーンを確認
```

### 最も頻繁に使用されるキーワード引数

```julia
* `data`                               # 観測 Dict または NamedTuple.
* `init`                               # 初期化 Dict または NT (デフォルト: -2 から +2).
```

### 戻り値

```julia
* `rc`                                 # 戻りコード、0 は成功を示す.
```

他のキーワード引数についての詳細なヘルプを参照してください ( `??stan_sample` )。

# 拡張ヘルプ

### 追加の設定キーワード引数

```julia
* `num_chains=4`                       # チェーンの数を更新します。

* `num_samples=1000`                   # サンプルの数。
* `num_warmups=1000`                   # ウォームアップサンプルの数。
* `save_warmup=false`                  # ウォームアップサンプルを保存します。

* `thin=1`                             # 薄める値を設定します。
* `refresh=100`                        # 出力の更新頻度。
* `seed=-1`                            # シード値を設定します。

* `test=:gradient`                     # テスト :gradient.
* `epsilon=1e-8`                       # 有限差分のステップサイズ。
* `error=1e-8`                         # エラー閾値。
```
