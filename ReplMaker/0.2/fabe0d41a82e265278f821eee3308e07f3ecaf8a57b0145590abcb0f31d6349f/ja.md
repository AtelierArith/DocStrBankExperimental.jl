```
         initrepl(parser::Function;
                  prompt_text = "myrepl> ",
                  prompt_color = :blue,
                  start_key = ')',
                  repl = Base.active_repl,
                  mode_name = :mylang,
                  show_function = nothing,
                  show_function_io = stdout,
                  valid_input_checker::Function = (s -> true),
                  keymap::Dict = REPL.LineEdit.default_keymap_dict,
                  completion_provider = REPL.REPLCompletionProvider(),
                  sticky = true,
                  startup_text=true
                  )
```

は、コードを受け取り、引数 `parser` に提供された任意の解析関数に従って解析するカスタムREPLモードを作成します。どのキーがREPLモードを初期化するかは `start_key` で選択し、REPLモードの名前は `mode_name` で指定し、オプションで与えられたREPL入力が解析前に有効かどうかをチェックする関数を `valid_input_checker` で提供できます。オートコンプリートオプションは、標準のJulia REPL TAB補完にデフォルトで設定されている `completion_provider` 引数を通じて提供されます。 `prompt_text` は文字列またはプロンプト文字列を計算するゼロ引数関数のいずれかである可能性があります。

REPLモードに入るための任意のキーの組み合わせはまだ許可されていませんが、現在は `CTRL` および `ALT`（別名 `META`）キーを修飾子として使用してREPLモードに入ることができます。たとえば、`initrepl` 関数にキーワード引数 `start_key="\C-g"` を渡すと、`CTRL` キーを押し続けて `g` を押すことで指定されたモードに入ることができます。

同様に、`start_key="\M-u"` を指定すると、`ALT`（別名 `META`）を押し続けて `u` を押すことで目的のモードに入ることができます。
