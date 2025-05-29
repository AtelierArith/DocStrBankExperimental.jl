FunctionOperatorは、多次元空間から別の多次元空間へのマッピングを行う演算子です。このマッピングは関数（`forw`）によって定義され、オプションで逆マッピング（`backw`）も定義できます。マッピングの入力は、AbstractArrayのサブタイプである必要があります。

以下のコンストラクタが利用可能です：

  * 位置引数コンストラクタ #1: `FunctionOperator{eltype}(forw, inDims, outDims)`
  * 位置引数コンストラクタ #2: `FunctionOperator{eltype}(forw, backw, inDims, outDims)`
  * 位置引数コンストラクタ #3: `FunctionOperator{eltype}(name, forw, inDims, outDims)`
  * 位置引数コンストラクタ #4: `FunctionOperator{eltype}(name, forw, backw, inDims, outDims)`
  * キーワードコンストラクタ: `FunctionOperator{eltype}(;kwargs...)`

ここで、`eltype`は入力配列の要素に対して強制される型です。

引数

  * `name::String`（オプションですが強く推奨）この文字列によって、演算子は後でエラーメッセージで参照されます。**警告！** これは（複合）FunctionOperatorsの等価性をチェックするためにも使用されます。デフォルト値: `OpX`（ここでXは各コンストラクタ呼び出しでインクリメントされる数字）。
  * `forw::Function` マッピングを定義する関数。1つまたは2つの引数を受け入れる必要があります。2つの引数の場合、最初の引数は結果を書き込むための事前割り当てされたバッファです（繰り返しの割り当てを避けることでコードを高速化します）。1つまたは2つの引数のいずれの場合でも、戻り値はマッピングの結果である必要があります。
  * `backw::Function`（オプション）backwと同様ですが、逆マッピングを定義します。
  * `inDims::Tuple{Vararg{Int}}` 入力配列のサイズ
  * `outDims::Tuple{Vararg{Int}}` 出力配列のサイズ
