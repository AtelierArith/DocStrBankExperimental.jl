```
setup_input(input_path::AbstractString, verbose::Bool, ext::String; paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}(), log_path::String="output_path", custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}())
```

手動で入力ファイルの拡張子を指定し、その後 [`setup_input(::AbstractString, ::Bool, ::InputExt, ::OrderedDict{String, Tuple{String, String}}, ::String, ::Vector{Tuple{String, String}})`](@ref) を実行します。

# 引数

  * `input_path::AbstractString`: 入力ファイルへのパス
  * `verbose::Bool`: `@debug` メッセージをログに記録するかどうか
  * `ext::String`: 手動の拡張子指定子
  * `paths::OrderedDict{String, Tuple{String, String}}=OrderedDict{String, Tuple{String, String}}`: 展開するパス。`paths` は [`SetupModule.default_paths`](@ref) とマージされ、`paths` が優先されます。`paths` の構文については [`SetupModule.default_paths`](@ref) を参照してください。
  * `log_path::String="output_path"`: ログ出力のためのディレクトリの `"path_name"`。`log_path` は `paths` に存在する必要があるか、[`SetupModule.default_paths`](@ref) によって定義される必要があります。
  * `custom_metadata::Vector{Tuple{String, String}}=Vector{Tuple{String, String}}()`: 作成日と `input_path` に加えて、入力ファイルに含める追加のメタデータ。
