```
notebooktolatex(notebook, targetdir="./build_latex"; template=:book, fontpath=nothing)
```

ノートブックファイルを取り込み、LaTeXに変換し、図、フォント、リストファイルを含むファイル構造を作成します。

  * `targetdir` は、LaTeXプロジェクトが作成されるターゲットディレクトリです。

ディレクトリが存在しない場合は、作成されます。

  * `template` - LaTeXファイルのテンプレート。LaTeXテンプレートに基づいています。

現在サポートされているテンプレートは `:book`、 `:mathbook` です。

  * `fontpath` - 出力されるLaTeXファイルは、JuliaでサポートされているユニコードをサポートするためにJuliaMonoフォントを使用します。ユーザーがすでにJuliaMonoをインストールしている場合、`.ttf`ファイルが保存されているパスを提供できます。`nothing`が渡されると、フォントファイルはダウンロードされ、`./fonts/`フォルダに保存されます。
