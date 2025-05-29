```
AWSBatchManager(max_workers; kwargs...)
AWSBatchManager(min_workers:max_workers; kwargs...)
AWSBatchManager(min_workers, max_workers; kwargs...)
```

[Amazon Web Services Batch](https://aws.amazon.com/batch/) サービスを介してワーカーを生成するクラスター マネージャー。通常、AWS Batch ジョブ内で追加リソースを追加するために使用されます。生成されるワーカーの数は、リソースの競合により、要求された `max_workers` よりも少なくなる可能性があります。 `min_workers` を指定することで、要求された `max_workers` よりも少ない数で起動を成功させることができます。

## 引数

  * `min_workers::Int`: 生成するワーカーの最小数。そうでない場合は例外がスローされます。
  * `max_workers::Int`: 生成するワーカーの要求数。

## キーワード

  * `definition::AbstractString`: ジョブのプロパティを決定する AWS Batch ジョブ定義の名前。これには、Docker イメージ、IAM ロール、および実行するコマンドが含まれます。
  * `name::AbstractString`: AWS Batch 内のジョブの名前。
  * `queue::AbstractString`: ワーカーが提出されるジョブキュー。キュー名またはキューの Amazon リソース名 (ARN) のいずれかです。設定されていない場合は、環境変数 "WORKER*JOB*QUEUE" にデフォルト設定されます。
  * `memory::Integer`: ジョブコンテナのメモリ制限 (MiB 単位)。この値を超えるとコンテナは終了します。
  * `region::AbstractString`: API リクエストが送信され、新しいワーカーが生成されるリージョン。デフォルトは "us-east-1" です。[AWS バッチの利用可能なリージョン](http://docs.aws.amazon.com/general/latest/gr/rande.html#batch_region) は AWS ドキュメントで確認できます。
  * `timeout::Period`: ワーカーが利用可能になるまで待機する最大秒数。欠落しているワーカーなしで進行しようとする前に待機します。

## 例

```julia
julia> addprocs(AWSBatchManager(3))  # 実行中の AWS バッチ ジョブ内から実行する必要があります
```
