```
application_config(port::String, impl::String, fname::String)
```

単一の遷移を持つワークフローアプリケーションを構成するための便利なコンストラクタ。

# 引数

  * `ports::String`: ワークフロー遷移のために構成するポート。
  * `impl::String`: ワークフロー遷移によって呼び出される実装を含むJuliaファイル。
  * `fnames::String`: ワークフロー遷移によって実行される関数名。

他にも [`Workflow_PetriNet`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref) を参照してください。
