CodeTrackingはInteractiveUtilsの拡張として考えることができ、Revise.jlと組み合わせて使用するのに適しています。

  * `code_string`, `@code_string`: メソッド定義のソースコード（文字列として）を取得します
  * `code_expr`, `@code_expr`: メソッド定義の式を取得します
  * `definition`: 上記の低レベルのバリアント
  * `pkgfiles`: パッケージを定義するソースファイルに関する情報を返します
  * `whereis`: メソッドに関する位置情報を返します（Reviseを使用すると、ファイルを編集する際に更新されます）
  * `signatures_at`: 指定された位置にまたがるすべてのメソッドのシグネチャを返します
