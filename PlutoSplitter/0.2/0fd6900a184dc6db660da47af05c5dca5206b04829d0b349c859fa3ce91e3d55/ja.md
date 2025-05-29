ノートブックファイルを分割します。

  * `notebookfile`: 分割するファイル。
  * `type`: 実行する分割のタイプ。 "check" はいくつかのサニティチェックのみを実行し、"statement" または "solution" です。

キーワード引数:

  * `output_filename`, オプション: 処理されたノートブックを保存するファイル名。デフォルトでは `type` が元のファイル名に追加されます。 `output_filename` は、`notebookfile` と `type` の2つの引数を受け取り、新しいファイル名を文字列として返す関数でも構いません。
