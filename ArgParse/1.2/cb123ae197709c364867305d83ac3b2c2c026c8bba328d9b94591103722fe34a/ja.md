```
ArgParseSettings
```

`ArgParseSettings`オブジェクトは、引数解析中に使用されるすべての設定を含んでいます。設定は一般設定と引数テーブル関連設定の2つのグループに分かれています。引数テーブルは、[`@add_arg_table!`](@ref)のような専門的な関数を定義して操作する必要がありますが、一般設定は単にオブジェクトフィールド（ほとんどが`Bool`または`String`）であり、キーワード引数としてコンストラクタに渡すことができ、いつでも直接設定することができます。

現在利用可能な一般設定のリストは次のとおりです：

  * `prog`（デフォルト = `""`）：自動生成されたヘルプおよび使用画面に表示されるプログラムの名前。空のままにすると、ソースファイル名が使用されます。
  * `description`（デフォルト = `""`）：プログラムの動作を説明するもので、自動生成されたヘルプ画面に、使用行と引数の説明の間に表示されます。`preformatted_description`が`false`の場合（下記参照）、自動的にフォーマットされますが、文字列内で2つの連続した改行を使用することで改行を強制し、非改行スペース（文字`'\ua0'`）を使用してスペースを手動で制御することができます。
  * `preformatted_description`（デフォルト = `false`）：`description`の自動フォーマットを無効にします。
  * `epilog`（デフォルト = `""`）：`description`のように、ヘルプ画面の引数説明の後に表示されます。同じフォーマットルールが適用されます。
  * `preformatted_epilog`（デフォルト = `false`）：`epilog`の自動フォーマットを無効にします。
  * `usage`（デフォルト = `""`）：ヘルプ画面および解析中にエラーが見つかったときに表示される使用行。空のままにすると、自動生成されます。
  * `version`（デフォルト = `"Unknown version"`）：バージョン情報。`:show_version`アクションで使用されます。
  * `add_help`（デフォルト = `true`）：`true`の場合、引数テーブルに`--help, -h`オプション（`:show_help`アクションをトリガー）が追加されます。
  * `add_version`（デフォルト = `false`）：`true`の場合、引数テーブルに`--version`オプション（`:show_version`アクションをトリガー）が追加されます。
  * `help_width`（デフォルト = `70`）：ヘルプテキストの幅を設定します。ユーザーが提供した場合、`usage`行には影響しません。また、`preformatted_description/epilog`オプションが`false`に設定されている場合、`description/epilog`行にも影響しません。
  * `help_alignment_width`（デフォルト = `24`）：オプションと引数名がリストされるヘルプテキストの左列の最大幅を設定します。これは、自動生成された場合の使用行のインデントにも影響します。4以上で、`help_width`未満である必要があります。
  * `fromfile_prefix_chars`（デフォルト = `Set{Char}()`）：これらの文字のいずれかで始まる引数は、引数が1行ごとに読み込まれるファイルを指定します。英数字とハイフンマイナス（`'-'`）は禁止されています。
  * `autofix_names`（デフォルト = `false`）：`true`の場合、オプション名や宛先のダッシュ（`'-'`）とアンダースコア（`'_'`）の使用を自動的に修正しようとします：すべてのアンダースコアは長いオプション名でダッシュに変換されます。また、関連する宛先名が自動生成される場合（[引数名](@ref)セクションを参照）、長いオプションと位置引数の両方でダッシュがアンダースコアに置き換えられます。たとえば、`"--my-opt"`として宣言されたオプションは、デフォルトでキー`"my_opt"`に関連付けられます。このオプションは、`parse_args`の引数`as_symbols=true`で解析する際にオンにすることを特にお勧めします。
  * `error_on_conflict`（デフォルト = `true`）：`true`の場合、引数テーブルに競合するエントリが追加された場合にエラーをスローします。`false`の場合、後のエントリが静かに優先されます。この設定が`false`のときの競合が何であるか、正確な動作についての詳細な説明は[競合とオーバーライド](@ref)セクションを参照してください。
  * `suppress_warnings`（デフォルト = `false`）：`true`の場合、すべての警告が抑制されます。
  * `allow_ambiguous_opts`（デフォルト = `false`）：`true`の場合、`-1`のようなあいまいなオプションが受け入れられます。
  * `commands_are_required`（デフォルト = `true`）：`true`の場合、コマンドは必須となります。[コマンド](@ref)セクションを参照してください。
  * `exc_handler`（デフォルト = `ArgParse.default_handler`）：これは、解析中にエラーが検出されたときに呼び出される関数です（例：オプションが認識されない、必須引数が渡されないなど）。2つの引数を取ります：`settings::ArgParseSettings`オブジェクトと`err::ArgParseError`例外。デフォルトのハンドラーは、スクリプトから呼び出されるか、インタラクティブ環境（例：REPL/IJulia）から呼び出されるかによって異なる動作をします。非インタラクティブ（スクリプト）モードでは、`ArgParse.cmdline_handler`を呼び出し、エラーテキストと使用画面を標準エラーに印刷し、エラーコード1でJuliaを終了します：

    ```julia
    function cmdline_handler(settings::ArgParseSettings, err, err_code::Int = 1)
        println(stderr, err.text)
        println(stderr, usage_string(settings))
        exit(err_code)
    end
    ```

    インタラクティブモードでは、代わりに`ArgParse.debug_handler`関数を呼び出し、エラーを再スローします。
  * `exit_after_help`（デフォルト = `!isinteractive()`）：`:show_help`または`:show_version`アクションがトリガーされたときに、エラーコード`0`でJuliaを終了します。`false`の場合、これらのアクションは単に解析を停止し、`parse_args`を`nothing`で返します。

使用例は次のとおりです：

```julia
settings = ArgParseSettings(description = "このプログラムは何かを行います",
                            commands_are_required = false,
                            version = "1.0",
                            add_version = true)
```

これは次のように等価です：

```julia
settings = ArgParseSettings()
settings.description = "このプログラムは何かを行います。"
settings.commands_are_required = false
settings.version = "1.0"
settings.add_version = true
```

省略形として、`description`フィールドはキーワードなしで渡すことができ、これにより上記と等価になります：

```julia
settings = ArgParseSettings("このプログラムは何かを行います。",
                            commands_are_required = false,
                            version = "1.0",
                            add_version = true)
```

ほとんどの設定は`parse_args`が呼び出されるまで効果を持ちませんが、いくつかは即座に効果を持ちます：`autofix_names`、`error_on_conflict`、`suppress_warnings`、`allow_ambiguous_opts`。
