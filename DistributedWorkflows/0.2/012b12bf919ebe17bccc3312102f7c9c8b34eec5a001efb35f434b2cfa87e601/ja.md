```
application_config(ports::Vector{String}, impl::String, fnames::Vector{String})
```

複数の遷移が同じファイルから実装の詳細を取得するワークフローアプリケーションを構成するための便利なコンストラクタです。

# 引数

  * `ports::Vector{String}`: ワークフロー遷移のために構成するポートのリスト。
  * `impl::String`: ワークフロー遷移によって呼び出される実装を含むJuliaファイル。
  * `fnames::Vector{String}`: ワークフロー遷移によって実行される関数名のリスト。

詳細については [`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref) を参照してください。
