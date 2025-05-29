```
@RemoteFile name url [key=value...]
```

`url`にある`RemoteFile`を変数`name`に割り当てます。

以下のキーワード引数が利用可能です：

  * `file`: 異なるローカルファイル名を設定します。
  * `dir`: ダウンロードディレクトリ。`dir`が設定されていない場合、RemoteFilesは現在のパッケージのルートの下に新しいディレクトリ`data`を作成し、そこにファイルを保存します。
  * `updates`（デフォルト: `:never`）：リモートファイルが更新される頻度を示します。可能な値は：

      * `:never`
      * `:daily`
      * `:monthly`
      * `:yearly`
      * `:mondays`/`:weekly`、`:tuesdays`など。
  * `retries`（デフォルト: 3）：試行すべきリトライの回数。
  * `try_backends`（デフォルト: `true`）：異なるバックエンドでリトライするかどうか。
  * `backends`（デフォルト `RemoteFiles.BACKENDS`）：試すバックエンド。
  * `wait`（デフォルト: 5）：リトライの間に待機する秒数。
  * `failed`（デフォルト: `:error`）：ダウンロードが失敗した場合に何をするか。例外をスローする（`:error`）か、警告を表示する（`:warn`）か。
