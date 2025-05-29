setPixel(o,r,b,g[, channel=0, command=0])

指定された `channel` で与えられた `command` を使用して、同じ長さの三つの `NTuples{N,UInt8}` で表されたピクセルの色を OPC サーバー `o` に送信します。

# 入力

  * `o::OpenPixelConnection` – 色を送信するサーバーを表す接続
  * `r`,`g`,`b::NTuple{N,UInt8}` – 同じ長さ `N` の `UInt8` の三つの `NTuple` で、各エントリのセットが一つのピクセルの色を表す 8 ビットの RGB 色の配列
  * `channel::Integer` – （`0`）値を送信するチャンネル/ストランド `[1-255]` を決定します。デフォルトの `0` はすべてのチャンネルを指します
  * `command::Integer` – （`0`）ピクセルを送信するために使用するコマンド。値 `0` は [openpixelcontrol.org](https://openpixelcontrol.org) によるデフォルトです
