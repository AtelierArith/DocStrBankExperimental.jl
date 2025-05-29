```
value = JUA_Server_readValue(server::JUA_Server, nodeId::JUA_NodeId, type = Any)
```

は、サーバーAPIを使用して`server`から`nodeId`の値を読み取ります。出力は可能であれば自動的にJulia型（Float64、String、Vector{String}など）に変換されます。それ以外の場合、open62541の複合型が返されます。

注意: `nodeId`内にどのような型の値が格納されているかは読み取る前には不明であるため、この関数は本質的に型不安定です。

オプション引数`type`を指定することで型の安定性が向上します。たとえば、`nodeId`にMatrix{Float64}が格納されていることがわかっている場合は、これを指定するべきです。間違った型が指定された場合、関数はTypeErrorをスローします。
