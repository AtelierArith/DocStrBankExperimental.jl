```
LocalQuantumJob(device::Union{String, BraketDevice}, source_module::String; kwargs...)
```

`device`（管理されたシミュレーター、QPU、または[埋め込みシミュレーター](https://docs.aws.amazon.com/braket/latest/developerguide/pennylane-embedded-simulators.html)）を使用し、`source_module`にあるコード（単一ファイル、Juliaパッケージ、またはPythonモジュールのいずれか）を実行する`LocalQuantumJob`を作成して起動します。`device`は、デバイスのARNを`String`として指定するか、[`BraketDevice`](@ref)で指定できます。*ローカル*ジョブは、`docker`を使用してジョブコンテナをローカルで起動することにより、*ローカル*で実行されます。ジョブは完了するまでブロックされ、[`AwsQuantumJob`](@ref)の`wait_until_complete`の動作を再現します。

キーワード引数`kwargs`は、ジョブの起動構成を制御します。

# キーワード引数

  * `entry_point::String` - `source_module`がPythonモジュール/Juliaパッケージの場合に実行する関数。デフォルトは空文字列で、この場合の動作はコード言語によって異なります。Pythonでは、ジョブは`source_module`内の`main`という関数を見つけて実行しようとします。Juliaでは、`source_module`が読み込まれ、Juliaの[`include`](https://docs.julialang.org/en/v1/base/base/#Base.include)で実行されます。
  * `image_uri::String` - ジョブを実行するためのECR内のDockerイメージのURI。デフォルトは空文字列で、この場合は[ベースコンテナ](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-script-environment.html)が使用されます。
  * `job_name::String` - ジョブの名前で、[ジョブコンソール](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-first.html)に表示されます。デフォルトはコンテナイメージ名と現在の時間の組み合わせです。
  * `code_location::String` - コードがアップロードされるS3プレフィックスURI。デフォルトは`default_bucket()/jobs/<job_name>/script`です。
  * `role_arn::String` - `LocalQuantumJob`には使用されません。
  * `hyperparameters::Dict{String, Any}` - ジョブに提供されるハイパーパラメータで、ジョブが実行されるときに環境変数から利用可能になります。詳細については[Amazon Braketのドキュメント](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-hyperparameters.html)を参照してください。
  * `input_data::Union{String, Dict}` - ジョブに提供するトレーニング/入力データに関する情報。`Dict`はチャネル名をローカルパスまたはS3 URIにマッピングする必要があります。`String`としてエンコードされた任意のローカルパスに見つかった内容は、`s3://{default_bucket_name}/jobs/{job_name}/data/{channel_name}`にS3にアップロードされます。ローカルパスまたはS3 URIが提供されると、デフォルトのチャネル名`"input"`が与えられます。デフォルトは`Dict()`です。
  * `instance_config::InstanceConfig` - `LocalQuantumJob`には使用されません。
  * `distribution::String` - `LocalQuantumJob`には使用されません。
  * `stopping_condition::StoppingCondition` - ジョブが強制的に停止される前に実行できる最大時間（秒単位）。デフォルトは`StoppingCondition(5 * 24 * 60 * 60)`です。
  * `output_data_config::OutputDataConfig` - ジョブの出力の場所を指定します。ここに保存されたデータは、[`download_result`](@ref)および[`results`](@ref)で利用可能になります。デフォルトは`OutputDataConfig("s3://{default_bucket_name}/jobs/{job_name}/data")`です。
  * `copy_checkpoints_from_job::String` - 現在のジョブで使用するチェックポイントのジョブARNを指定します。この値を指定すると、`use_checkpoints_from_job`の`checkpoint_config` S3 URIから現在のジョブの`checkpoint_config` S3 URIにチェックポイントデータがコピーされ、ジョブ実行中に`checkpoint_config.localPath`で利用可能になります。デフォルトはチェックポイントをコピーしないこと（空文字列）です。
  * `checkpoint_config::CheckpointConfig` - *この*ジョブのチェックポイントデータを保存する場所を指定します。デフォルトは`CheckpointConfig("/opt/jobs/checkpoints", "s3://{default_bucket_name}/jobs/{job_name}/checkpoints")`です。
  * `tags::Dict{String, String}` - このジョブにタグ付けするためのキーと値のペアを指定します。
