```
IndexNode{T,I}
```

インデックスツリーインターフェースを実装するツリーのノード。このようなツリーは、デフォルトで`getindex`を呼び出す[`nodevalue`](@ref)の二引数メソッドを使用してノードを取得できるオブジェクト`tree`で構成されています。

`IndexNode`はツリーインターフェースを実装しており、インデックスツリーインターフェースを実装するオブジェクトからツリーインターフェースを実装するものへのアダプターと考えることができます。

`IndexNode`はノードに関連付けられた値を保存しませんが、[`nodevalue`](@ref)を呼び出すことでそれを取得できます。

## コンストラクタ

```julia
IndexNode(tree, node_index)

IndexNode(tree) = IndexNode(tree, rootindex(tree))  # 一引数コンストラクタは`rootindex`を必要とします
```

ここで`tree`はツリー全体の構造に関する情報を保存または取得できるオブジェクトであり、`node_index`は`node_index`が構築されるノードのインデックスです。
