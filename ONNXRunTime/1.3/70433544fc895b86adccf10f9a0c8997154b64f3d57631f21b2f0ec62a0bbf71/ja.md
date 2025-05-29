```julia
load_inference(
    path::AbstractString;
    execution_provider,
    envname,
    logging_level,
    provider_options
) -> ONNXRunTime.InferenceSession

```

指定された`path`にあるONNXファイルを推論セッションにロードします。

*キーワード引数:*

  * `execution_provider`: `:cpu`または`:cuda`のいずれか。後者はCUDA対応のGPUを必要とし、最初に`CUDA`および`cuDNN`パッケージをインポートする必要があります。
  * `envname`: ロギング目的で使用される名前。
  * `logging_level`: 診断出力のレベル。オプションは`:verbose`、`:info`、`:warning`（デフォルト）、`:error`、および`:fatal`です。
  * `provider_options`: 実行プロバイダーに渡されるオプションを含む名前付きタプル。

注意: C APIの`CreateEnv`関数の制限により、`envname`と`logging_level`はプロセスごとに一度だけ設定できます。これらを変更しようとする試みは無視されます。
