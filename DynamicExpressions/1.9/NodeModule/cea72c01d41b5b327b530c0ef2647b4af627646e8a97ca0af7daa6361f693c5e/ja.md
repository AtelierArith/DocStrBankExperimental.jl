```
copy_node(tree::AbstractExpressionNode; break_sharing::Val{BS}=Val(false)) where {BS}
```

ノードをコピーし、すべての子ノードを再帰的にコピーします。これは組み込みのコピーよりも効率的です。

`break_sharing`が`Val(true)`に設定されている場合、ツリー内の共有は無視されます。
