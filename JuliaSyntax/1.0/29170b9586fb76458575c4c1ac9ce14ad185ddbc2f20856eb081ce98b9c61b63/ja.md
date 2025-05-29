```
build_tree(make_node::Function, ::Type{StackEntry}, stream::ParseStream; kws...)
```

ParseStreamから深さ優先探索を使用してツリーを構築します。`make_node`は次のシグネチャを持つ必要があります。

```
make_node(head::SyntaxHead, span::Integer, children)
```

ここで、`children`は葉ノードの場合は`nothing`、内部ノードの場合は`StackEntry`型の子ノードの反復可能なものである必要があります。`StackEntry`はノード型である可能性がありますが、ツリーを構築する際に必要な他の情報を含むこともあります。

ParseStreamが最上位レベルで複数のノードを持つ場合、`K"wrapper"`がそれらを単一のノードにラップするために使用されます。

ここでのツリーは後順で深さ優先に構築されます。
