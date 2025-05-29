```
runtests(files; subs = common_subs(), mod = nothing, quiet = false, exitfirst = false, maxfail = nothing) :: Bool
```

指定されたMarkdownファイルを読み込み、埋め込まれたテストケースを抽出して実行します。ディレクトリが渡された場合、そのディレクトリ内のすべての`*.md`ファイルを読み込みます。この関数は、テストが成功した場合に`true`を返し、そうでない場合は`false`を返します。

`subs`を指定して、期待される出力に適用される置換をカスタマイズし、正規表現に変換します。

`mod`を指定して、指定されたモジュールのコンテキストでテストを実行します。

`quiet = true`を設定すると、エラーレポート以外のすべての出力が抑制されます。

`exitfirst = true`を設定すると、最初のエラーまたは失敗で終了します。あるいは、`maxfail`を使用して許容される最大エラー数または失敗数を設定します。

```
runtests(; default = common_args(), subs = common_subs(), mod = nothing, quiet = false, exitfirst = false, maxfail = nothing)
```

この形式では、テストファイルがコマンドラインパラメータとして指定されます。パラメータなしで呼び出すと、プログラムディレクトリ内の`*.md`ファイルからテストが読み込まれ、`default`パラメータを使用して上書きできます。この関数は、テストが成功した場合にコード`0`でプログラムを終了し、そうでない場合は`1`を返します。

`test/runtests.jl`でこの形式を使用します：

```julia
using NarrativeTest
NarrativeTest.runtests()
```
