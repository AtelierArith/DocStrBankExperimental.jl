setPixel(o,colors[, channel=0, command=0])

指定された `channel` と指定された `command` で OPC サーバー `o` にピクセル `colors` を送信します。

# 入力

  * `o::OpenPixelConnection` – 色を送信するサーバーを表す接続
  * `colors::Array{<:AbstractRGB}` – 各エントリが1つのピクセルの色を表す RGB 色の配列
  * `channel::Integer` – （`0`）値を送信するチャンネル/ストランド `[1-255]` を決定します。デフォルトの `0` はすべてのチャンネルを指します
  * `command::Integer` – （`0`）ピクセルを送信するために使用するコマンド。値 `0` は [openpixelcontrol.org](https://openpixelcontrol.org) によるデフォルトです
