```
IteratedModel(model;
    controls=MLJIteration.DEFAULT_CONTROLS,
    resampling=Holdout(),
    measure=nothing,
    retrain=false,
    advanced_options...,
)
```

指定された監視付き `model` を指定された反復 `controls` でラップします。ここで `model` は反復をサポートする必要があり、これは (`iteration_parameter(model)` が `nothing` でない場合) に真となります。

利用可能なコントロール: Step(), Info(), Warn(), Error(), Callback(), WithLossDo(), WithTrainingLossesDo(), WithNumberDo(), Data(), Disjunction(), GL(), InvalidValue(), Never(), NotANumber(), NumberLimit(), NumberSinceBest(), PQ(), Patience(), Threshold(), TimeLimit(), Warmup(), WithIterationsDo(), WithEvaluationDo(), WithFittedParamsDo(), WithReportDo(), WithMachineDo(), WithModelDo(), CycleLearningRate() および Save()。

!!! 重要     コントロールに対してサンプル外の損失を利用可能にするために、ラップされた `model` はデータの一部でのみ訓練され、反復が進行します。ユーザーは、コントロールされた反復が終了した後にすべてのデータで再訓練を強制したい場合は、`retrain=true` を指定することができます。詳細は「トレーニング」と、以下の「拡張ヘルプ」の `retrain` オプションを参照してください。

# 拡張ヘルプ

# オプション

  * `controls=Any[IterationControl.Step(1), EarlyStopping.Patience(5), EarlyStopping.GL(2.0), EarlyStopping.TimeLimit(Dates.Millisecond(108000)), EarlyStopping.InvalidValue()]`: コントロールは [https://JuliaAI.github.io/MLJ.jl/dev/getting_started/](https://JuliaAI.github.io/MLJ.jl/dev/controlling_iterative_models/) で要約されていますが、詳細や高度なオプションについては個々のドキュメント文字列を照会してください。独自のコントロールを作成するには、前述のドキュメントを参照してください。
  * `resampling=Holdout(fraction_train=0.7)`: デフォルトのリサンプリングは、パフォーマンスのサンプル外推定（「損失」）を計算するためにデータの30%を保持します（`WithLossDo` などの損失ベースのコントロール用）。すべてのデータをコントロールされた反復に使用する場合は、`resampling=nothing` を指定し、各サンプル外の損失を最新のトレーニング損失に置き換えます。これはモデルがこれを利用可能にする場合（`supports_training_losses(model) == true`）。モデルがトレーニング損失を報告しない場合は、代わりに `resampling=InSample()` を使用できます。それ以外の場合、`resampling` は `Holdout` 型であるか、形式 `(train_indices, test_indices)` の要素を1つ持つベクターでなければなりません。
  * `measure=nothing`: モデルのパフォーマンスを推定するための StatisticalMeasures.jl 互換の測定値（「損失」、ただし方向は重要ではありません - つまり、これはスコアである可能性があります）。デフォルトで推測されます。`resampling=nothing` の場合は無視されます。
  * `retrain=false`: `retrain=true` または `resampling=nothing` の場合、`iterated_model` は元の `model` とまったく同じように動作しますが、反復パラメータが自動的に選択されます（「学習」）。つまり、コントロールされた反復が停止した後、モデルは*すべての*利用可能なデータで再訓練され、同じ回数の反復が使用されます。これは、反復モデルをさらにラップする場合や、パイプラインや他の複合モデルに挿入する場合に通常望まれます。`retrain=false`（デフォルト）で、`resampling` が `Holdout` の場合、`iterated_model` は提供されたデータのサブセットで訓練された元のモデルのように動作します。
  * `weights=nothing`: 測定値に渡される観察ごとの重み; 指定されていない場合、これらは均一であると理解されます。
  * `class_weights=nothing`: 測定値に渡されるクラス重み; 指定されていない場合、これらは均一であると理解されます。
  * `operation=nothing`: 測定値によって消費されるターゲット値またはプロキシターゲット値を計算するための操作（`predict` または `predict_mode` など）; デフォルトで自動的に推測されます。
  * `check_measure=true`: トレーニングデータとの互換性のために `measure` のチェックをオーバーライドするには `false` を指定します。
  * `iteration_parameter=nothing`: `model` の反復パラメータを名前付けするシンボル（例: `:epochs`）; デフォルトで推測されます。提供された `model` の反復パラメータの実際の値は無視されます; ラップされたモデルのトレーニング中に内部クローンの値のみが変更されます。
  * `cache=true`: 反復パラメータの増分間にデータのモデル固有の表現がキャッシュされるかどうか; メモリを速度よりも優先するには `cache=false` を指定します。

# トレーニング

`IteratedModel` のインスタンス `iterated_model` をいくつかの `data` でトレーニングする（例えば、マシンにバインドして `fit!` を呼び出すことによって）と、以下のアクションが実行されます：

  * `resampling !== nothing` の場合、`data` は指定された `resampling` 戦略に従って *train* と *test* セットに分割されます。
  * ラップされたモデルのクローン `model` が内部マシン `train_mach` のトレインデータにバインドされます。`resampling === nothing` の場合は、すべてのデータが代わりに使用されます。このマシンはコントロールが適用されるオブジェクトです。例えば、`Callback(fitted_params |> print)` は `fitted_params(train_mach)` の値を印刷します。
  * クローンの反復パラメータが `0` に設定されます。
  * 指定された `controls` が順番に `train_mach` に繰り返し適用され、コントロールの1つが停止をトリガーするまで続きます。損失ベースのコントロール（例: `Patience()`, `GL()`, `Threshold(0.001)`）は、予測とテストターゲット値に `measure` を適用することによって得られるサンプル外の損失を使用します。（具体的には、これらの予測は `operation(train_mach)` によって返されるものです。）`resampling === nothing` の場合は、最新のトレーニング損失が代わりに使用されます。一部のコントロールはサンプル外の損失とトレーニング損失の*両方*を必要とします（例: `PQ()`）。
  * 停止がトリガーされると、`retrain == false`（デフォルトで真）または `resampling === nothing` でない限り、すべての `data` にクローンの `model` がバインドされ、以下の `mach_production` というマシンにバインドされます。

# 予測

上記の例で `predict(mach, Xnew)` を呼び出すと、`predict(mach_production, Xnew)` が返されます。`predict_mean`, `predict_mode`, `predict_median` に対しても同様の文が成り立ちます。

# パラメータを変更するコントロール

コントロールは `train_mach.model`（`model` のクローン）のフィールド（ハイパーパラメータ）を変更することが許可されています。例えば、学習率を変更するには、次のコントロールを使用することができます。

```
Callback(mach -> mach.model.eta = 1.05*mach.model.eta)
```

ただし、`model` がそのパラメータの変更に関してウォームリスタートをサポートしていない限り、これは `train_mach` の再訓練をゼロからトリガーし、異なるトレーニング結果をもたらすため、推奨されません。

# ウォームリスタート

次の例では、2回目の `fit!` 呼び出しは、`model` がウォームリスタートをサポートしていると仮定して、内部の `train_mach` のトレーニングを再起動しません。

```julia
iterated_model = IteratedModel(
    model,
    controls = [Step(1), NumberLimit(100)],
)
mach = machine(iterated_model, X, y)
fit!(mach) # 100回の反復でトレーニング
iterated_model.controls = [Step(1), NumberLimit(50)],
fit!(mach) # *追加* で50回の反復でトレーニング
```

一般的に、`iterated_model` が変更され、再度 `fit!(mach)` が呼び出されると、変更されるパラメータが `model` または `controls` またはその両方だけである場合、ウォームリスタートが試みられます。

具体的には、`train_mach.model` が現在の `iterated_model.model` の値に一致するように変更され、後者の反復パラメータが前回の `fit!(mach)` 呼び出しで使用された最後の値に更新されます。次に、（更新された）コントロールの繰り返し適用が新たに始まります。 ```
