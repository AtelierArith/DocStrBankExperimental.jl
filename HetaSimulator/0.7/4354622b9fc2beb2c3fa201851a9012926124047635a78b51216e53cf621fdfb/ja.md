```
heta_build(
  target_dir::AbstractString;
  declaration::String = "platform",
  units_check::Bool = false,
  log_mode::String = "error",
  log_path::String = "build.log",
  log_level::String = "info",
  debug::Bool = false,
  dist_dir::String = "dist",
  meta_dir::String = "meta",
  source::String = "index.heta",
  type::String = "heta",
  export_::Union{String, Nothing} = nothing,
)
```

Hetaベースのプラットフォームからモデルをビルドします

詳細については `heta compiler` ドキュメントを参照してください: [https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options](https://hetalang.github.io/#/heta-compiler/cli-references?id=running-build-with-cli-options)

引数:

  * `target_dir` : Hetaプラットフォームディレクトリへのパス
  * `declaration` : 宣言ファイルへのパス。デフォルトは `"platform"`
  * `units_check` : `true` に設定すると、単位の整合性がチェックされます
  * `log_mode` : ログモード。デフォルトは `"error"`
  * `log_path` : ログファイルへのパス。デフォルトは `"build.log"`
  * `log_level` : 表示するログレベル。デフォルトは `"info"`
  * `debug` : デバッグモードをオンにします。デフォルトは `false`
  * `dist_dir` : 配布物を書き込むディレクトリパス。デフォルトは `"dist"`
  * `meta_dir` : メタディレクトリパス。デフォルトは `"meta"`
  * `source` : メインのhetaモジュールへのパス。デフォルトは `"index.heta"`
  * `type` : ソースファイルのタイプ。デフォルトは `"heta"`
  * `export_` : モデルを指定されたフォーマットにエクスポートします: `Julia,JSON`, `{format:SBML,version:L3V1},JSON`
