```
preorder!(net::HybridNetwork)
```

属性 `net.vec_node` を更新し、ノードが前順（トポロジカルソートとも呼ばれる）であるようにし、各ノードがその親ノードの後に訪問されるようにします。`preorder!` を呼び出す前に、エッジの方向が正しい必要があります。これには `directedges!` を使用します。
