```
NodePattern <: AbstractNodeLike
```

`NodePattern` は、グラフ内のノードをマッチさせるために使用できる `Node`-のようなオブジェクトです。

`IDType` を使用して、IDによるマッチングや他のプロパティによるマッチングを可能にします。`IDType` が何もない場合、パターンはラベルとプロパティによってマッチします。それ以外の場合、最初にIDによってマッチを開始します。

`NodePattern` と `Node` の唯一の違いは、`NodePattern` がIDを持たない可能性があることです。
