```
arity(φ::SyntaxTree)::Integer
arity(tok::Connective)::Integer
```

`Connective`または`SyntaxTree`の`arity`を返します。`arity`は、ツリー内のノードに許可される子の数を表す整数です。`arity`が0、1、または2の`Connective`は、それぞれ`nullary`、`unary`、および`binary`と呼ばれます。`SyntaxLeaf`（`Atom`および`Truth`値）は常にnullaryです。

参照：[ `SyntaxLeaf`](@ref)、[ `Connective`](@ref)、[ `SyntaxBranch`](@ref)。
