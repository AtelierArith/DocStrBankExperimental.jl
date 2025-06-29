```
convert(::Type{Node}, md::Markdown.MD) -> Node
convert(::Type{Node{M}}, md::Markdown.MD, meta=M) where M -> Node{M}
```

標準ライブラリのMarkdown ASTをMarkdownAST表現に変換します。

サブツリーを変換することはできないことに注意してください。`MD`オブジェクトのみが変換可能です。結果は、[`Document`](@ref)をルート要素とするツリーになります。

渡された型引数が`Node`の場合、結果のツリーはデフォルトのノード型`Node{Nothing}`のオブジェクトで構成されます。ただし、カスタムメタデータフィールドの型`M`を持つMarkdownASTツリーに変換することも可能であり、その場合、`M`型にはゼロ引数のコンストラクタが利用可能でなければならず、新しい`Node`オブジェクトが構築されるたびに呼び出されます。

また、`.meta`オブジェクトを構築するためにカスタム関数を使用することも可能で、`meta`引数はゼロ引数メソッドを持つ呼び出し可能なオブジェクトでなければならず、新しいノードが構築されるたびに呼び出されます。
