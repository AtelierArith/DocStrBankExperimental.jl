```
add_arg_group!(settings, description, [name , [set_as_default]]; keywords...)
```

この関数は、`settings`の引数テーブルに引数グループを追加します。`description`は、そのグループのタイトルとしてヘルプ画面で使用される`String`です。`name`は、そのグループを後で参照するために提供できる一意の名前です。

グループは相互排他的および/または必須として宣言できます。以下を参照してください。

この関数を呼び出した後、[`@add_arg_table!`](@ref)マクロおよび[`add_arg_table!`](@ref)関数のすべての後続の呼び出しは、新しいグループをデフォルトとして使用します。ただし、`set_as_default`が`false`に設定されている場合を除きます（デフォルトは`true`で、`name`を提供する場合にのみ設定できます）。したがって、最も明白な使用パターンは、各グループについてそれを追加し、そのグループの引数テーブルを populated することです。例：

```julia-repl
julia> settings = ArgParseSettings();

julia> add_arg_group!(settings, "custom group");

julia> @add_arg_table! settings begin
          "--opt"
          "arg"
       end;

julia> parse_args(["--help"], settings)
usage: <command> [--opt OPT] [-h] [arg]

optional arguments:
  -h, --help  show this help message and exit

custom group:
  --opt OPT
  arg
```

例からわかるように、新しいグループは常に既存のグループの最後に追加されます。

`name`は`Symbol`としても渡すことができます。禁止されている名前は、標準グループ名（`"command"`、`"positional"`および`"optional"`）およびハッシュ文字`'#'`で始まる名前です。

グループを相互排他的として宣言するには、キーワード`exclusive = true`を使用します。相互排他的グループにはオプションのみを含めることができ、引数やコマンドは含めることができず、グループから複数のオプションが提供されると解析は失敗します。

グループを必須として宣言するには、`required = true`キーワードを使用します。この場合、グループから少なくとも1つのオプションまたは位置引数またはコマンドを提供する必要があります。
