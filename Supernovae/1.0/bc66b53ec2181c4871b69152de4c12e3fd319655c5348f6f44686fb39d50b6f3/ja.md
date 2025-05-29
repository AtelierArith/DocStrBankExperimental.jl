```
main(toml_path::AbstractString, verbose::Bool, profile::Bool)
```

`toml_path`を読み込み、`verbose`に基づいてログの詳細度を設定します。[`run_Supernovae`](@ref)を実行し、`profile`が`true`の場合は、コードのプロファイリングも行います。

# 引数

  * `toml_path::AbstractString`: toml入力ファイルへのパス。
  * `verbose::Bool`: ログの詳細度を設定
  * `profile::Bool`: trueの場合、[`run_Supernovae`](@ref)をプロファイル
