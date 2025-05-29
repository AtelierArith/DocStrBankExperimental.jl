```
node_depth(root::AbstractRuleNode, node::AbstractRuleNode)::Int
```

`root`を根とする[`AbstractRuleNode`](@ref)ツリーにおける`node`の深さを返します。深さは`root == node`のときに`1`です。

!!! warning
    この関数が機能するためには、`node`は`root`の部分木でなければなりません。

