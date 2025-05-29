コードの読み込みの問題により、このモジュールは `atreplinit` を使用して読み込まれると正しく機能しません。Juliaが起動する際にコマンドライン引数を使用して読み込む必要があります：

例:   julia -i -e "using VimBindings; VimBindings.init()"
