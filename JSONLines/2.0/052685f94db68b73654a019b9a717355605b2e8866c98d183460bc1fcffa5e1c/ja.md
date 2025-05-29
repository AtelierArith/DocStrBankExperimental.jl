@MStructType name fieldnames...

このマクロは、JSONLinesファイルから特定の変数を読み取るための可変`StructType`を宣言するための便利な構文を提供します。また、結果の型の行に対して`row[:col]`アクセスを定義します。

  * `name`: `StructType`の名前
  * `fieldnames...`: 読み取る変数の名前（ファイル内と同じでなければなりません）
