### 抽象型 AbstractUDPConnection <: Toolips.AbstractConnection

`AbstractUDPConnection` は `Toolips.AbstractConnection` と同じ役割を果たします - レスポンスハンドラーに渡される可変型です。`Connection` はその後、`respond!`、`send`、およびその `packet` フィールドと共に使用され、レスポンスを処理するためのデータを作成して送信します。

  * 参照: `UDPConnection`、`UDPIOConnection`、`start!`

##### 一貫性

  * `ip`**::String**
  * `port`**::Int64**
  * `packet`**::String**
  * `data`**::Dict{Symbol, Any}**
