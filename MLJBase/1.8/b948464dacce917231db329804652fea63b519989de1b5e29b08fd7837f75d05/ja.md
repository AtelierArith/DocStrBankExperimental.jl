```
PerformanceEvaluation <: AbstractPerformanceEvaluation
```

[`evaluate`](@ref)（モデルとデータ用）または[`evaluate!`](@ref)（マシン用）によって返されるオブジェクトの型。このようなオブジェクトは、教師ありモデルまたは外れ値検出モデルのパフォーマンス（一般化誤差）の推定値をエンコードし、計算に付随する他の情報を格納します。

`compact=true`オプションで[`evaluate`](@ref)または[`evaluate!`](@ref)が呼び出されると、代わりに[`CompactPerformanceEvaluation`](@ref)オブジェクトが返されます。

`evaluate`/`evaluate!`が呼び出されると、提供されたオプションに従って、行インデックスのトレイン/テストペア（「フォールド」）が生成されます。行は観測に対応します。生成されたトレイン/テストペアは、`PerformanceEvaluation`構造体の`train_test_rows`フィールドに記録され、対応する推定値は、`measure`に記録された各測定（メトリック）ごとに1つのエントリを持つベクトル`measurement`に集約されます。

表示されると、`PerformanceEvaluation`オブジェクトは、`per_fold`エントリの標準誤差から導出された`1.96*SE`という見出しの下に値を含みます。この値は、与えられた`measurement`の正式な95％信頼区間を構築するのに適しています。このような区間は注意して解釈する必要があります。例えば、[Bates et al. (2021)](https://arxiv.org/abs/2104.00673)を参照してください。

### フィールド

これらのフィールドは、`PerformanceEvaluation`構造体のパブリックAPIの一部です。

  * `model`: パフォーマンス評価を作成するために使用されたモデル。チューニングモデルの場合、これは見つかった最良のモデルです。
  * `measure`: パフォーマンスを評価するために使用される測定（メトリック）のベクトル
  * `measurement`: 各`measure`の要素ごとに1つの測定を持つベクトル - すべてのトレイン/テストペア（フォールド）にわたるパフォーマンス測定を集約します。特定の測定`m`に適用される集約方法は`StatisticalMeasuresBase.external_aggregation_mode(m)`です（一般的には`Mean()`または`Sum()`）。
  * `operation`（例：`predict_mode`）：評価される予測を生成するために各測定に適用される操作。可能性は：`predict`、`predict_mean`、`predict_mode`、`predict_median`、または`predict_joint`です。
  * `per_fold`: 個々のテストフォールド評価のベクトルのベクトル（測定ごとに1つのベクトル）。パフォーマンス推定の分散の粗い推定を取得するのに役立ちます。
  * `per_observation`: 個々の観測ごとの測定を含むベクトルのベクトル：評価`e`に対して、`e.per_observation[m][f][i]`は、`m`番目の測定を使用して評価された`f`番目のテストフォールドの`i`番目の観測の測定です。ハイパーパラメータ最適化のいくつかの形式に役立ちます。特定の測定`measure`の集約測定は、`StatisticalMeasures.can_report_unaggregated(measure) == true`の場合、フォールド内のすべての観測にわたって繰り返されます。`e`が`per_observation=false`オプションで計算された場合、`e_per_observation`は`missings`のベクトルです。
  * `fitted_params_per_fold`: リサンプリング中にトレーニングされた各マシン`mach`の`fitted params(mach)`を含むベクトル - トレイン/テストペアごとに1つのマシン。各個別のトレーニングイベントの学習されたパラメータを抽出するために使用します。
  * `report_per_fold`: リサンプリング中にトレーニングされた各マシン`mach`の`report(mach)`を含むベクトル - トレイン/テストペアごとに1つのマシン。
  * `train_test_rows`: 各トレインとテストがトレーニングと評価のための行（観測）インデックスのベクトルであるタプルのベクトルで、形式は`(train, test)`です。
  * `resampling`: トレイン/テストペアを生成するためにユーザーが指定したリサンプリング戦略（または直接指定されたリテラルなトレイン/テストペア）。
  * `repeats`: リサンプリング戦略が繰り返された回数。

[`CompactPerformanceEvaluation`](@ref)も参照してください。
