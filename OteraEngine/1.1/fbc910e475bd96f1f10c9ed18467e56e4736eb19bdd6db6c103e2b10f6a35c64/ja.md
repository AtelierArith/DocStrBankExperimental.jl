```
Template(
    txt::String;
    path::Bool=true,
    config_path::String="",
    config::Dict{String, String} = Dict()
)
```

これはこのパッケージの唯一の構造体と関数です。この構造体には4つのパラメータがあります。

  * `txt` はテンプレートファイルへのパスまたはString型のテンプレートです。
  * `path` はパラメータ `txt` がファイルパスを表すかどうかを決定します。デフォルト値は `true` です。
  * `config_path` は設定ファイルへのパスです。設定ファイルのサフィックスは `toml` でなければなりません。
  * `config` はテンプレートの設定です。これは `Dict` 型であり、詳細については [configuraiton](#Configurations) を参照してください。

# レンダリング

テンプレートを作成したら、コードを実行するだけです！これには、Template構造体のFunction-like Objectを使用します。`tmp(; init::Dict{Symbol, T}) where {T}` 変数は、名前（String）と値のペアを含む `init` Dictによって初期化されます。`init` を渡さない場合、初期化は行われません。

# 例

これはシンプルな使用例です：

```julia-repl
julia> using OteraEngine
julia> txt = "Hello {{ usr }}!"
julia> tmp = Template(txt, path = false)
julia> init = Dict(:usr=>"OteraEngine")
julia> tmp(init = init)
```
