抽象フォーマットタイプ。

フォーマットは、msgpackプリミティブを介して値をパッキングおよびアンパッキングするためのルールを決定します。これらはシングルトンタイプであることが期待されています。

新しいフォーマット `F <: Format` をサポートするには、[`pack`](@ref) と [`unpack`](@ref) の対応するメソッドを定義します。

このパッケージには、いくつかの組み込みフォーマットが付属しています。以下のコアフォーマットは、msgpack仕様の1つまたは複数のフォーマットに基づいて構築された低レベルの実装を持っています：

  * [`NilFormat`](@ref) (msgpack nil),
  * [`BoolFormat`](@ref) (msgpack boolean),
  * [`SignedFormat`](@ref) (msgpack negative / positive fixint, signed 8-64),
  * [`UnsignedFormat`](@ref) (msgpack positive fixint, unsigned 8-64),
  * [`FloatFormat`](@ref) (msgpack float32, float64)
  * [`StringFormat`](@ref) (msgpack fixstr, str 8-32),
  * [`BinaryFormat`](@ref) (msgpack bin 16, bin 32).
  * [`ExtensionFormat`](@ref) (msgpack fixext 1-8, ext 8-32)

ベクトルのようなオブジェクトやマップのようなオブジェクトには、さまざまな利点と欠点を持ついくつかの組み込みフォーマットが提供されています。これらは以下のサブタイプです：

  * [`AbstractVectorFormat`](@ref) (msgpack fixarray, array 16, array 32),
  * [`AbstractMapFormat`](@ref) (msgpack fixmap, map 16, map 32)。

追加の便利なフォーマットには以下が含まれます：

  * [`ArrayFormat`](@ref) (多次元配列を格納),
  * [`BinVectorFormat`](@ref) (ビットタイプ要素を持つベクトルを効率的に格納),
  * [`BinArrayFormat`](@ref) (多次元ビットタイプ配列を効率的に格納),
  * [`TypeFormat`](@ref) (型を格納)
  * [`TypedFormat`](@ref) (値とその型を格納して一般的なアンパッキングを可能にする)。
  * [`ContextFormat`](@ref) (特定のコンテキストをローカルに強制)。
