```
application_config(ports::Vector{String}, impl::Vector{String}, fnames::Vector{String})
```

複数の遷移を持つワークフローアプリケーションを構成するためのコンストラクタです。

# 引数

  * `ports::Vector{String}`: ワークフロー遷移のために構成するポートのリスト。
  * `impl::Vector{String}`: ワークフロー遷移によって呼び出される実装を含むjuliaファイルのリスト。
  * `fnames::Vector{String}`: ワークフロー遷移によって実行される関数名のリスト。

詳細は [`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref) を参照してください。
