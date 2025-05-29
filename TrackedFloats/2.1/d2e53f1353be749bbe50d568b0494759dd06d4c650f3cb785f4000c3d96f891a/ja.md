ロガーのためのすべての設定を含む構造体。

## フィールド

  * `filename::String` ログを書き込むファイルのベース名。

    コンストラクタは自動的にこのベース名の先頭にタイムスタンプを付加するため、ログは時系列でグループ化されます。
  * `buffersize::Int` ファイルに書き込む前にメモリにバッファリングするログの数。

    デフォルトは1000です。必要なログを取得せずにクラッシュする場合は減らしてください。
  * `printToStdOut::Bool` ログをSTDOUTに書き込むかどうか; デフォルトは`false`です。
  * `allErrors::Bool` すべてのエラーを`*_error_log.txt`ファイルに記録します。
  * `cstg::Bool` CSTG形式でログを書き込みます。
  * `cstgLineNum::Bool` CSTG出力に行番号を含めます。
  * `cstgArgs::Bool` CSTG出力に関数への引数を含めます。
  * `maxLogs::Union{Int,Unbounded}` ログするイベントの最大数; デフォルトは`Unbounded`です。
  * `maxFrames::Union{Int,Unbounded}` ロギングで印刷するスタックフレームの最大数; デフォルトは`Unbounded`です。
  * `exclusions::Array{Symbol}` ログしないイベント; デフォルトは`[:prop]`です。
