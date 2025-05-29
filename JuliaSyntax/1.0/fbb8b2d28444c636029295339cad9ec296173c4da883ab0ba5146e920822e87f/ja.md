```
SyntaxNode(source::SourceFile, raw::GreenNode{SyntaxHead};
           keep_parens=false, position::Integer=1)
```

`Expr`と似たレイアウトのASTノード。通常、[`parseall`](@ref)などのパーサAPI関数を呼び出すことでソーステキストから構築されます。
