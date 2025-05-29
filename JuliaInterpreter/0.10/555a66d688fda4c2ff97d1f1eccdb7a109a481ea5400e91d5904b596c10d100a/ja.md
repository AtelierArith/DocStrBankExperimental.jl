`Frame`は特定の呼び出しフレームにおける現在の実行状態を表します。フィールド：

  * `framecode`: このフレームの[`FrameCode`](@ref)。
  * `framedata`: このフレームの[`FrameData`](@ref)。
  * `pc`: このフレームのプログラムカウンタ（評価される次のステートメントの整数インデックス）。
  * `caller`: このフレームの親呼び出し元、または`nothing`。
  * `callee`: このフレームによって呼び出されたフレーム、または`nothing`。

`Base`関数`show_backtrace`と`display_error`はオーバーロードされており、`show_backtrace(io::IO, frame::Frame)`および`display_error(io::IO, er, frame::Frame)`は、それぞれバックトレースまたはエラーを表示します。これは、Baseがそれらを表示する方法に似ています。
