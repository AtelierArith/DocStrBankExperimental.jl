```
RedirectedCommand(source, destination)
```

`AbstractCommand`とファイル（`String`）をラップします。

これにより、コマンドからファイルへの出力リダイレクトや、ファイルからコマンドへの入力リダイレクトが可能になります。リダイレクトは、`RedirectedCommand`の`source`および`destination`パラメータによって指定されます。

# 引数

  * `source`: リダイレクト元。`source`が`String`の場合、読み取るファイルのファイル名を表します。`source`が`AbstractCommand`のサブタイプの場合、出力をリダイレクトするコマンドを表します。
  * `destination`: リダイレクト先。`destination`が`String`の場合、書き込むファイルのファイル名を表します。`destination`が`AbstractCommand`のサブタイプの場合、リダイレクトされた出力を入力として受け取るコマンドを表します。
