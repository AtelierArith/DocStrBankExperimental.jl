```
encodemoves(g::SimpleGame)::Vector{UInt8}
encodemoves(g::Game)::Vector{UInt8}
```

ゲームの手をバイトベクターとしてエンコードします。

これは、PGNよりもはるかにコンパクトなバイナリ形式でゲームを保存するのに便利です。

逆関数 `decodemoves` は、ゲームに戻すために使用されます。
