gtp_repl(genmove) は、ユーザーが提供した `genmove(board, color, info)` を呼び出す Go テキストプロトコルを実装した読み取り実行印刷ループ (REPL) を実行します。

Julia スクリプトに接続する Go クライアントは、通常、そのスクリプトが stdin/stdout で REPL を開始することを期待します。これは `gtp_repl` のデフォルトの動作です。代替の入力/出力ストリームは、'input' および 'output' キーワード引数を介して指定できます。

`name` および `version` キーワード引数を使用して、クライアントが要求した場合に通信される名前とバージョンを設定できます。
