stan_sample()

StanJuliaのSampleModel (<: CmdStanModel.) からサンプリングします。

## 必要な引数

```julia
* `m <: CmdStanModels`                 # SampleModel
```

### 最も頻繁に使用されるキーワード引数

```julia
* `data`                               # 観測値のDictまたはNamedTuple。
* `init`                               # 初期化のDictまたはNT（デフォルト：-2から+2）。
```

他のキーワード引数についての詳細なヘルプは、 `??stan_sample` を参照してください。

### 戻り値

```julia
* `rc`                                 # 戻りコード、0は成功。
```

# 拡張ヘルプ

### 追加の設定キーワード引数

```julia
* `num_threads=4`                      # C++スレッドの数を更新します。
* `check_num_chains=true`              # C++チェーンまたはJuliaレベルのチェーンをチェックします
* `num_cpp_chains=1`                   # C++チェーンの数を更新します。
* `num_julia_chains=1`                 # Juliaチェーンの数を更新します。
                                       # 両方ともnum_chainsから初期化されます

* `use_cpp_chains=false`               # C++レベルでnum_chainsを実行します
                                       # Juliaプロセスを使用するにはfalseに設定します

* `num_chains=4`                       # 実際のチェーンの数。
* `num_samples=1000`                   # サンプルの数。
* `num_warmups=1000`                   # ウォームアップサンプルの数。
* `save_warmup=false`                  # ウォームアップサンプルを保存します。

* `thin=1`                             # スリム値を設定します。
* `seed=-1`                            # シード値を設定します。

* `engaged=true`                       # 適応が有効です。
* `gamma=0.05`                         # 適応の正則化スケール。
* `delta=0.8`                          # 適応の目標受け入れ統計。
* `kappa=0.75`                         # 適応の緩和指数。
* `t0=10`                              # 適応の反復オフセット。
* `init_buffer=75`                     # 初期適応間隔。
* `term_buffer=50`                     # 最終的な高速適応間隔。
* `window=25`                          # 初期の遅い適応間隔。

* `algorithm=:hmc`                     # サンプリングアルゴリズム。
* `engine=:nuts`                       # :nutsまたは:static。
* `max_depth=10`                       # :nutsエンジンの最大ツリーデプス。
* `int_time=2 * pi`                    # :staticエンジンの統合時間。

* `metric=:diag_e`                     # 多様体設定の幾何学：
                                       # :diag_e、:unit_eまたは:dense_e。
* `metric_file=""`                     # 事前コンパイルされたユークリッドメトリック。
* `stepsize=1.0`                       # 離散進化のステップサイズ
* `stepsize_jitter=0.0`                # ステップサイズのランダムジッター（[%]）

* `use_json=true`                      # .Rデータファイルのためにfalseに設定します。

* `sig_figs=6`                         # 出力ファイルの有効数字の数

* `summary=true`                       # stansummary .csvファイルを作成します
* `print_summary=false`                # サマリーを表示します

* `show_logging=false`                 # ターミナルでログファイルの更新を表示します
```

注意：現在、C++レベルのチェーンとJuliaレベルのチェーンの両方を使用することはお勧めしません。デフォルトでは、 `use_cpp_chains` に基づいて `stan_sample()` メソッドは、 `num_cpp_chains=num_chains; num_julia_chains=1` （デフォルト）または `num_julia_chains=num_chains;num_cpp_chain=1` のいずれかを設定します。デフォルトの動作を防ぐために、 `stan_sample()` の呼び出しで `check_num_chains` キーワード引数を `false` に設定してください。

C++レベルのスレッドは、別々のチェーンを実行したり、特定の操作を高速化したりするために複数の方法で使用できます。デフォルトでは、StanSample.jlのSampleModelはC++のnum_threadsを4に設定します。例のディレクトリ内のRedCardsStudyの `graphs` サブディレクトリを参照してください。

通常、ユーザーはsig_figs=18で出力を生成することを検討すべきです。そうすることでf64が一意に識別されます。これにより.csvファイルのサイズが増加し（その後の読み取り時間に影響を与える可能性があります）。
