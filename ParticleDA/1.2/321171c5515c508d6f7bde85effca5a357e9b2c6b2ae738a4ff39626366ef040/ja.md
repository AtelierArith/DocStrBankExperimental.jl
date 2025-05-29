```
run_particle_filter(
    init_model,
    input_file_path,
    observation_file_path,
    filter_type=BootstrapFilter,
    summary_stat_type=MeanAndVarSummaryStat;
    rng=Random.TaskLocalRNG()
) -> Tuple{Matrix, Union{NamedTuple, Nothing}}
```

パーティクルフィルタを実行します。`init_model`はモデルを初期化する関数で、`input_file_path`は入力パラメータを含むYAMLファイルへのパスです。`observation_file_path`はフィルタリングを行う観測シーケンスを含むHDF5ファイルへのパスです。`filter_type`は使用するパーティクルフィルタのタイプです。可能な値については[`ParticleFilter`](@ref)を参照してください。`summary_stat_type`は各時間ステップで計算するパーティクルの要約統計のタイプを指定します。可能な値については[`AbstractSummaryStat`](@ref)を参照してください。`rng`はフィルタリング中にランダム変数を生成するために使用する乱数生成器です - 再現可能な結果を保証するためにシード付きの乱数生成器を指定することができます。複数のスレッドで実行する場合は、`Random.TaskLocalRNG`（デフォルト）などのスレッドセーフな生成器を使用する必要があります。

最終観測時間におけるフィルタリング分布の推定を表す状態パーティクルを含むタプル（各パーティクルが返される行列の列）と、この最終フィルタリング分布の推定要約統計を含む名前付きタプルを返します。MPIを使用して複数のランクで実行する場合、返される状態配列はこのランクにローカルなパーティクルにのみ対応し、要約統計はマスタランクでのみ返され、他のすべてのランクはその2番目の返り値に対して`nothing`を返します。
