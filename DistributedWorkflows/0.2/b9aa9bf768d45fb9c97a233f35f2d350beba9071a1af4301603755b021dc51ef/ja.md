```
submit_workflow(client, workflow, input_params::Vector)
```

クライアントインスタンスに設定されたワークフローを送信します。

# 引数

  * `client`: ワークフロークライアントインスタンス。
  * `workflow`: 設定されたワークフローオブジェクト。
  * `input_params::Vector`: ワークフロー実行のための入力リスト。

関連情報としては [`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref) を参照してください。
