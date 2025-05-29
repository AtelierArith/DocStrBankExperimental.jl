```
protojl(
    relative_paths::Union{String,Vector{String}},
    search_directories::Union{String,Vector{String},Nothing}=nothing,
    output_directory::Union{String,Nothing}=nothing;
    include_vendored_wellknown_types::Bool=true,
    always_use_modules::Bool=true,
    force_required::Union{Nothing,Dict{String,Set{String}}}=nothing,
    add_kwarg_constructors::Bool=false,
    parametrize_oneofs::Bool=false,
    common_abstract_type::Bool=false,
) -> Nothing
```

`search_directories`内の`relative_paths`にある`.proto`ファイルのためのJuliaコードを生成し、`output_directory`に保存します。

`package`指定子を持たない`{file_name}.proto`ファイルをコンパイルすると、`output_directory`に`{file_name}_pb.jl`が生成されます。`{file_name}.proto`が例えば`package foo_bar.baz_grok`を含む場合、次のディレクトリ構造が作成されます：

```bash
root  # `output_directory`引数からの`protojl`
└── foo_bar
    ├── foo_bar.jl  # モジュール`foo_bar`を定義し、`baz_grok`をインポート
    └── baz_grok
        ├── {file_name}_pb.jl
        └── baz_grok.jl  # モジュール`baz_grok`を定義し、`{file_name}_pb.jl`を含む
```

生成されたパッケージのトップレベルモジュール、すなわちこの例では`foo_bar.jl`を含める必要があります。すべてのインポートされた`.proto`ファイルもコンパイルされます。解決できない場合や`search_directories`内に見つからない場合はエラーが発生します。

# 引数

  * `relative_paths::Union{String,Vector{String}}`: コンパイルする`.proto`ファイルへのパスまたはパスのリスト。
  * `search_directories::Union{String,Vector{String},Nothing}=nothing`: `relative_paths`を検索するディレクトリまたはディレクトリのリスト。デフォルトでは、現在のディレクトリが使用されます。
  * `output_directory::Union{String,Nothing}=nothing`: 生成されたJuliaソースコードを保存するパス。省略すると、変換されたコードは一時ディレクトリに保存され、そのパスは@infoログとして表示されます。

# キーワード

  * `include_vendored_wellknown_types::Bool=true`: `ProtoBuf.VENDORED_WELLKNOWN_TYPES_PARENT_PATH`を`search_directories`に追加し、「よく知られた」メッセージ定義を利用可能にします。
  * `always_use_modules::Bool=true`: `.proto`ファイルに`package`指定子が含まれていなくても、モジュール内でjuliaコードを生成します。`{file_name}.proto`ファイルのモジュール名は`{file_name}_pb`です。
  * `force_required::Union{Nothing,Dict{String,Set{String}}}=nothing`: `message`および`oneof`フィールドが常に送信されると仮定します - その場合、これらのそれぞれの型を`Nothing`と`Union`する必要はありません。例えば：

```julia
# force_required === nothing
struct MyMessage
    message_field::Union{Nothing,MyOtherMessage}}
end
```

```julia
# force_required === Dict("{file_name}.proto" => Set(["MyMessage.message_field"]))
struct MyMessage
    message_field::MyOtherMessage}
end
```

  * `add_kwarg_constructors::Bool=false`: 各メッセージに対して、オプションのキーワード引数を持つ外部コンストラクタを生成します（フィールドが必須のメッセージである場合、デフォルト値はなく、キーワード引数はオプションではありません）。
  * `parametrize_oneofs::Bool=false`: 生成された親構造体に型パラメータとして`OneOf`型を追加します。すなわち、これは次のように変更します：

```julia
# parametrize_oneofs == false
struct MyMessage
    oneof_field::Union{Nothing, OneOf{<:Union{Int, String}}}
end
```

を

```julia
# parametrize_oneofs == true
struct MyMessage{T1<:Union{Nothing, OneOf{<:Union{Int, String}}}}
    oneof_field::T1
end
```

  * `common_abstract_type::Bool=false`: `true`の場合、すべての生成された構造体は`ProtoBuf.AbstractProtoBufMessage`のサブタイプになります。

# 注意

相対パスを使用して`import`文を解決するために、`relative_paths`と`search_directories`を絶対パスの代わりに使用します。
