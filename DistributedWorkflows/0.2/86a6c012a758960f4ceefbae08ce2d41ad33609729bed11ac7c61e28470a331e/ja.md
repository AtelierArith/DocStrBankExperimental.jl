```
client(workers::Int, nodefile::String, rif_strategy::String)
```

ワークフロー実行インフラストラクチャを設定してクライアントを構成し、開始します。nodefileは、指定された場所に存在しない場合、または`rif_strategy`が`local`の場合にローカルホスト名で自動的に populated されます。

# 引数

  * `workers::Int`: ノードごとに起動されるワーカーの数。
  * `nodefile::String`: nodefileの場所。
  * `rif_strategy::String`: ワークフローインフラストラクチャの起動モード。複数のノードにわたってワーカーを分散させるための`ssh`またはローカルホストのみで実行するための`local`を受け入れます。

関連情報としては、[`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref)があります。
