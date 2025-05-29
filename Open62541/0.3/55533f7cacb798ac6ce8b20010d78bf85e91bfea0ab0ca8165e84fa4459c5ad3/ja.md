```
value = JUA_Client_readValueAttribute(client::JUA_Client, nodeId::JUA_NodeId, type = Any)
```

は、`client`が接続されているサーバーから`nodeId`の値を読み取るためにクライアントAPIを使用します。

出力`value`は、可能であれば自動的にJulia型（Float64、String、Vector{String}など）に変換されます。そうでない場合は、open62541の複合型が返されます。

注意: `nodeId`内にどのような型の値が格納されているかは読み取る前には不明なため、この関数は本質的に型が不安定です。

オプション引数`type`が提供されると型の安定性が向上します。たとえば、`nodeId`にMatrix{Float64}が格納されていることがわかっている場合は、これを指定するべきです。間違った型が指定された場合、関数はTypeErrorをスローします。
