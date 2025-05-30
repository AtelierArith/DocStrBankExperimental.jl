```
sharedpathmatrix(net::HybridNetwork; checkpreorder::Bool=true)
```

この関数は、ネットワーク内のすべてのノード間の共有パス行列を計算します。ネットワークが前順序であると仮定します。checkpreorderがtrue（デフォルト）である場合、事前にネットワークに対して関数`preorder!`を実行します。

[`MatrixTopologicalOrder`](@ref)型のオブジェクトを返します。
