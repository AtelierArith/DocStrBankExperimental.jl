`FileIO` API（簡潔な概要、詳細は各関数を参照）：

  * `format"PNG"`：特定の定義されたフォーマットを指定
  * [`File{fmt}`](@ref) および [`Stream{fmt}`](@ref)：リソースが特定のフォーマット `fmt` を持つことを宣言するオブジェクトのタイプ
  * [`load([filename|stream])`](@ref)：フォーマットされたファイルからデータを読み込み、フォーマットを推測
  * `load(File{format"PNG"}(filename))`：フォーマットを手動で指定
  * [`loadstreaming([filename|stream])`](@ref)：`load` に似ているが、読み取ることができるオブジェクトを返す
  * [`save(filename, data...)`](@ref)：データを保存する際の類似操作
  * [`savestreaming([filename|stream])`](@ref)：`save` に似ているが、書き込むことができるオブジェクトを返す
  * `io = open(f::File, args...)`：ファイルを開く
  * [`io = stream(s::Stream)`](@ref stream)：クエリオブジェクト `s` から IOStream を返す
  * [`query([filename|stream])`](@ref)：`filename` のフォーマットを推測しようとする
  * [`unknown(q)`](@ref)：クエリが解決できない場合は true を返す
  * [`skipmagic(io, fmt)`](@ref)：`io` の位置をマジックバイトの直後に設定
  * [`magic(fmt)`](@ref)：フォーマット `fmt` のマジックバイトを返す
  * [`info(fmt)`](@ref)：フォーマット `fmt` の `(magic, extensions)` を返す
  * [`add_format(fmt, magic, extension, libraries...)`](@ref)：新しいフォーマットを登録
  * [`add_loader(fmt, :Package)`](@ref)：`Package` がタイプ `fmt` のファイルの読み込みをサポートしていることを示す
  * [`add_saver(fmt, :Package)`](@ref)：`Package` がタイプ `fmt` のファイルの保存をサポートしていることを示す
