```
workflow_config(workflow::String, output_dir::String, app_config::Vector{Application_config})
```

クライアントインスタンスによる実行のためにワークフローを構成します。

# 引数

  * `workflow::String`: ワークフローの名前。
  * `output_dir::String`: ワークフロー実行中に生成される出力データを保存する場所。
  * `app_config::Vector{Application_config}`: ワークフロー実行のためのアプリケーション構成のリスト。

関連情報としては [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref) を参照してください。
