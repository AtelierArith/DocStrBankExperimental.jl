```
NodeSplit <: Operation
```

NodeSplit操作。入力ノードをその親の数だけのノードに分割します。これは[`NodeReduction`](@ref)の逆操作です。

# 成功する適用の要件

ノードは次の条件を満たす場合に分割できます：

  * グラフに存在する。
  * 親が少なくとも2つある。

[`is_valid_node_split_input`](@ref)を使用して、これらの要件を`@assert`できます。

参照：[`can_split`](@ref)
