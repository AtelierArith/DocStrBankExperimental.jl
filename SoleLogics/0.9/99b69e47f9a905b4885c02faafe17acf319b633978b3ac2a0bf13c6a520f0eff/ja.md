```
abstract type SyntaxTree <: AbstractSyntaxStructure end
```

[構文木](https://en.wikipedia.org/wiki/Abstract_syntax_tree)のための抽象型；すなわち、構文葉（`SyntaxLeaf`、例えば`Truth`値や`Atom`など）と、それらの`Connective`（すなわち`SyntaxBranch`）による構成。

!!! note
    `SyntaxTree`は*ランク付き木*であり、`AbstractTrees`インターフェースに従うべきであることに注意してください。


また[`SyntaxLeaf`](@ref)、[`SyntaxBranch`](@ref)、[`AbstractSyntaxStructure`](@ref)、[`Formula`](@ref)も参照してください。
