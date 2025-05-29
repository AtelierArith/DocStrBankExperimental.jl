```julia
UDPConnection <: AbstractUDPConnection
```

  * ip**::String**
  * port**::Int64**
  * packet**::String**
  * data**::Dict{Symbol, Any}**
  * server**::Sockets.UDPSocket**

---

`UDPConnection`はあなたの`UDPHandler`の関数に渡されます。これは本質的に`ToolipsUDP`における入出力ストリームです。私たちは`send`と`respond!`を使用して応答し、`c.packet`フィールドを呼び出すことで受信パケットを取得します。

##### コンストラクタ

  * `UDPConnection(data::Dict{Symbol, Any}, server::Sockets.UDPSocket)`
