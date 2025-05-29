```
client(workers::Int, nodefile::String, rif_strategy::String, log_host::String, log_port::Int)
```

ワークフロー実行インフラストラクチャを設定し、ログサービスに接続するクライアントを構成して開始します。nodefileは、指定された場所に存在しない場合、または`rif_strategy`が`local`の場合にローカルホスト名で自動的に populated されます。

# 引数

  * `workers::Int`: ノードごとに起動されるワーカーの数。
  * `nodefile::String`: nodefileの場所。
  * `rif_strategy::String`: ワークフローインフラストラクチャの起動モード。複数のノードにワーカーを分散させるための`ssh`またはローカルホストのみで実行するための`local`を受け入れます。
  * `log_host::String`: ログサービスのホスト。
  * `log_port::Int` : ログサービスがリッスンしているポート。

詳細については、[`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref)を参照してください。
