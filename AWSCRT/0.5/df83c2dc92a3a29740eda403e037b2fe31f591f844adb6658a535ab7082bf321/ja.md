環境変数:

  * `AWS_CRT_MEMORY_TRACING`: メモリトレースを有効にするには `0`、`1`、または `2` に設定します。デフォルトはオフです。`aws_mem_trace_level` を参照してください。
  * `AWS_CRT_MEMORY_TRACING_FRAMES_PER_STACK`: メモリトレースのスタックごとのフレーム数を設定します。デフォルトはAWSライブラリのデフォルトです。
  * `AWS_CRT_LOG_LEVEL`: ロギングを有効にするには `0` から `6` に設定します。デフォルトはオフです。[`aws_log_level`](https://juliaservices.github.io/LibAwsCommon.jl/dev/#LibAwsCommon.aws_log_level) を参照してください。
  * `AWS_CRT_LOG_PATH`: ログファイルのパスを設定します。`AWS_CRT_LOG_LEVEL` が設定されている場合は設定する必要があります。

注意: このパッケージ内のアンダースコアで始まるすべてのシンボルはプライベートであり、このパッケージの公開インターフェースの一部ではありません。使用しないでください。
