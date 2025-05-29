[`Face`](@ref)は、テキストを表示するためのグラフィカル属性のコレクションです。フェイスは、ターミナルや他の場所でテキストがどのように表示されるかを制御します。

ほとんどの場合、[`Face`](@ref)は、*フェイス名*シンボルとの一意の関連付けとしてグローバルフェイス辞書に保存され、この名前で参照されることが最も多いです。

# 属性

すべての属性はキーワードコンストラクタを介して設定でき、デフォルトは`nothing`です。

  * `height`（`Int`または`Float64`）：デシポイント（`Int`の場合）またはベースサイズの因子（`Float64`の場合）での高さ。
  * `weight`（`Symbol`）：最も薄いものから最も濃いものまでのシンボルの1つ `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold`, または `:black`。ターミナルでは、`:normal`より大きい任意のウェイトは太字として表示され、可変輝度テキストをサポートするターミナルでは、`:normal`より小さい任意のウェイトは薄く表示されます。
  * `slant`（`Symbol`）：シンボルの1つ `:italic`, `:oblique`, または `:normal`。
  * `foreground`（`SimpleColor`）：テキストの前景色。
  * `background`（`SimpleColor`）：テキストの背景色。
  * `underline`、テキストの下線で、次のいずれかの形式を取ります：

      * `Bool`：テキストに下線を引くべきかどうか。
      * `SimpleColor`：この色でテキストに下線を引くべき。
      * `Tuple{Nothing, Symbol}`：シンボルによって設定されたスタイル（`:straight`, `:double`, `:curly`, `:dotted`, または `:dashed`のいずれか）を使用してテキストに下線を引くべき。
      * `Tuple{SimpleColor, Symbol}`：指定されたSimpleColorでテキストに下線を引き、前述のシンボルによって指定されたスタイルを使用するべき。
  * `strikethrough`（`Bool`）：テキストに打ち消し線を引くべきかどうか。
  * `inverse`（`Bool`）：前景色と背景色を反転させるべきかどうか。
  * `inherit`（`Vector{Symbol}`）：継承するフェイスの名前で、早いフェイスが優先されます。すべてのフェイスは`:default`フェイスから継承します。
