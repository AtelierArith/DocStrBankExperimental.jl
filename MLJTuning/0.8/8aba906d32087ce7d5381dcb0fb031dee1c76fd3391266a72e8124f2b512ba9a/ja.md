```
tuned_model = TunedModel(; model=<モデルを変異させる>,
                         tuning=RandomSearch(),
                         resampling=Holdout(),
                         range=nothing,
                         measure=nothing,
                         n=default_n(tuning, range),
                         operation=nothing,
                         other_options...)
```

教師あり学習者のハイパーパラメータ最適化のためのモデルラッパーを構築し、`tuning`戦略と変異させるハイパーパラメータを持つ`model`を指定します。

```
tuned_model = TunedModel(; models=<比較するモデル>,
                         resampling=Holdout(),
                         measure=nothing,
                         n=length(models),
                         operation=nothing,
                         other_options...)
```

最適なモデルの選択のための複数の`models`のラッパーを構築します（上記の`model=v[1]`および`range=v`を指定することに相当します）。イテレータ`models`の要素は共通の型を持つ必要はありませんが、すべてが`Deterministic`またはすべてが`Probabilistic`でなければなりません *これはチェックされません* が、最初の生成された要素から推測されます。

以下にオプションの完全なリストを示します。

### トレーニング

`mach=machine(tuned_model, X, y)`または`mach=machine(tuned_model, X, y, w)`で`fit!(mach)`を呼び出すと：

  * `range`で指定されたハイパーパラメータの変異を持つ`model`のクローンを検索し、指定された`measure`を最適化するモデルを見つけるための検索を開始します。指定された`tuning`戦略と`resampling`戦略を使用して実施されるパフォーマンス評価を使用します。`models`が明示的にリストされている場合、検索は代わりにイテレータ`models`によって生成されたモデルに対して行われます。
  * 最適なモデル`fitted_params(mach).best_model`に基づいて内部マシンをフィットさせ、最適な`model`オブジェクトをすべての提供されたデータ`X`、`y`（、`w`）でラップします。`predict(mach, Xnew)`を呼び出すと、この内部マシンの`Xnew`に対する予測が返されます。最終的なトレーニングは`train_best=false`を設定することで抑制できます。

### 検索空間

サポートされる`range`オブジェクトは、指定された`tuning`戦略に依存します。詳細については`strategy`のドキュメントを参照してください。同じ型のモデルの明示的なリスト`v`に対して最適化するには、`strategy=Explicit()`を使用し、`model=v[1]`および`range=v`を指定します。

検索されるモデルの数は`n`で指定されます。指定されていない場合、`MLJTuning.default_n(tuning, range)`が使用されます。`n`が増加し、再度`fit!(mach)`が呼び出されると、古い検索履歴が復元され、検索は中断したところから続行されます。

### 測定（メトリクス）

複数の`measure`が指定されている場合、最初のもののみが最適化されます（`strategy`が多目的でない限り）が、指定されたすべての測定に対するパフォーマンスが計算され、`report(mach).best_performance`および生成されたレポートの他の関連属性に報告されます。観測ごとの重みやクラス重みを測定に渡すオプションがあります。以下を参照してください。

*重要。* カスタム測定`my_measure`が使用され、測定が損失ではなくスコアである場合、`MLJ.orientation(my_measure) == :score`を確認して、測定の最大化が行われることを確認してください。誤った値は`MLJ.orientation(::typeof(my_measure)) = :score`で上書きします。

### フィットしたパラメータおよびその他のトレーニング（チューニング）結果へのアクセス

パフォーマンス推定のPlots.jlプロットは`plot(mach)`または`heatmap(mach)`によって返されます。

チューニングマシン`mach`が上記のようにトレーニングされた後、`fitted_params(mach)`には以下のキー/値があります：

|                  key |             value |
| --------------------:| -----------------:|
|         `best_model` |      最適なモデルインスタンス |
| `best_fitted_params` | 最適なモデルの学習されたパラメータ |

名前付きタプル`report(mach)`には以下のキー/値が含まれます：

|                  key |                             value |
| --------------------:| ---------------------------------:|
|         `best_model` |                      最適なモデルインスタンス |
| `best_history_entry` |          対応する履歴のエントリ、パフォーマンス推定を含む |
|        `best_report` | 最適なモデルをすべてのデータにフィットさせた結果生成されたレポート |
|            `history` |              チューニング戦略特有のすべての評価の履歴 |

および`tuning`戦略に特有の他のキー/値ペア。

`history`の各要素は、以下のプロパティを持つプロパティアクセス可能なオブジェクトです：

|           key |                                                          value |
| -------------:| --------------------------------------------------------------:|
|     `measure` |                                                 測定（メトリクス）のベクトル |
| `measurement` |                                              測定ごとのベクトル、1つの測定ごと |
|    `per_fold` |                                         未集約の各フォールド測定のベクトルのベクトル |
|  `evaluation` | 完全な`PerformanceEvaluation`/`CompactPerformaceEvaluation`オブジェクト |

### キーワードオプションの完全なリスト

  * `model`: 評価のためにクローンされ、変異させる`Supervised`モデルプロトタイプ
  * `models`: 明示的に評価されるMLJモデルのイテレータ。これらは異なる型を持つ場合があります。
  * `tuning=RandomSearch()`: 適用されるチューニング戦略（例、`Grid()`）。完全なオプションのリストについては、MLJマニュアルの[Tuning Models](https://alan-turing-institute.github.io/MLJ.jl/dev/tuning_models/#Tuning-Models)セクションを参照してください。
  * `resampling=Holdout()`: パフォーマンス評価に適用されるリサンプリング戦略（例、`Holdout()`、`CV()`、`StratifiedCV()`）
  * `measure`: パフォーマンス評価に適用される測定または測定；最適化には最初のもののみが使用されます（戦略が多目的でない限り）が、すべてが履歴に報告されます
  * `weights`: パフォーマンス評価において測定に渡される観測ごとの重み。サポートを確認するには`supports_weights(measure)`を使用します。
  * `class_weights`: パフォーマンス評価において測定に渡されるクラス重み。サポートを確認するには`supports_class_weights(measure)`を使用します。
  * `repeats=1`: リサンプリングでトレイン/テストセットを複数回生成するため（「モンテカルロ」リサンプリング）；詳細については[`evaluate!`](@ref)を参照してください
  * `operation`/`operations` - `predict`、`predict_mean`、`predict_mode`、`predict_median`、または`predict_joint`のいずれか、または`measure`/`measures`と同じ長さのこれらのベクトル。指定しない場合は自動的に推測されます。
  * `range`: 範囲オブジェクト；チューニング戦略のドキュメントはサポートされるタイプを説明します
  * `selection_heuristic`: 最適なモデルが決定されるルール。デフォルトのヒューリスティック`NaiveSelection()`によれば、`measure`（または`measure`の最初の要素）は各リサンプルに対して評価され、これらの各フォールド測定が集約されます。測定が`：loss`（または`：score`）の場合、最も低い（または最も高い）集約を持つモデルが選択されます。
  * `n`: 繰り返しの数（すなわち、評価されるモデルの数）；指定しない場合はチューニング戦略によって設定されます
  * `train_best=true`: 最適なモデルをトレーニングするかどうか
  * `acceleration=default_resource()`: これをサポートするチューニング戦略の並列化モード
  * `acceleration_resampling=CPU1()`: リサンプリングの並列化モード
  * `check_measure=true`: `measure`が指定された`model`および`operation`と互換性があるかどうかを確認するかどうか
  * `cache=true`: ユーザー提供データのモデル固有の表現をキャッシュするかどうか；メモリを節約するために`false`に設定します。速度の向上は、`resampling isa Holdout`の場合に限られる可能性があります。
  * `compact_history=true`: `CompactPerformanceEvaluation`](@ref)または通常の[`PerformanceEvaluation`](@ref)オブジェクトを履歴に書き込むかどうか（`:evaluation`キーを介してアクセスされる）；コンパクト形式はメモリを節約するためにいくつかのフィールドを除外します。
  * `logger=default_logger()`: モデルのパフォーマンス評価を外部に報告するためのロガー、例えば`MLJFlow.Logger`インスタンス。起動時、`default_logger()=nothing`；グローバルロガーを設定するには`default_logger(logger)`を使用します。
