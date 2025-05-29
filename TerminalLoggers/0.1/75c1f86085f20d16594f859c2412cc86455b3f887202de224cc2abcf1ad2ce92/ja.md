```
TerminalLogger(stream=stderr, min_level=LogLevel(-1); meta_formatter=default_metafmt,
               show_limited=true, right_justify=0)
```

テキストコンソール（例えば、Julia REPL）でのインタラクティブな可読性に最適化されたフォーマットのロガーです。これは、デフォルトでJuliaにインストールされているターミナルロガー`Logging.ConsoleLogger`の拡張版です。

`min_level`未満のログレベルはフィルタリングされます。

メッセージのフォーマットは、キーワード引数を設定することで制御できます：

  * `meta_formatter`は、ログイベントのメタデータ`(level, _module, group, id, file, line)`を受け取り、ログメッセージのための色（`printstyled`に渡されるものと同様）、プレフィックス、サフィックスを返す関数です。デフォルトは、ログレベルでプレフィックスを付け、モジュール、ファイル、行位置を含むサフィックスを付けることです。
  * `show_limited`は、大きなデータ構造の印刷を画面に収まるものに制限します。これは、フォーマット中に`:limit` `IOContext`キーを設定することによって行われます。
  * `right_justify`は、ログメタデータが右揃えされる整数列です。デフォルトはゼロ（メタデータは独自の行に配置されます）です。
