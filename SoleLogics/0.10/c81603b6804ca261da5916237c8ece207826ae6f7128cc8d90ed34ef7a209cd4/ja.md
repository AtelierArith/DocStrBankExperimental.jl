```
abstract type SyntaxTree <: SyntaxStructure end
```

[構文木](https://en.wikipedia.org/wiki/Abstract_syntax_tree)のための抽象型；すなわち、構文葉（`SyntaxLeaf`、例えば`Truth`値や`Atom`など）と、`Connective`（すなわち`SyntaxBranch`）を介したそれらの構成。

`SyntaxTree`は*ランク付き木*であり、`AbstractTrees`インターフェースを実装する（べき）ことに注意してください。

# インターフェース

  * `children(φ::SyntaxTree)::NTuple{N,SyntaxTree} where N`
  * `token(φ::SyntaxTree)::Connective`
  * さらに[`SyntaxStructure`](@ref)も参照

# ユーティリティ関数

  * `tokentype(φ::SyntaxTree)`
  * `arity(φ::SyntaxTree)::Int`

# その他のユーティリティ関数（木を歩く必要がある）

  * `Base.in(tok::SyntaxToken, φ::SyntaxTree)::Bool`
  * `height(φ::SyntaxTree)::Int`
  * `tokens(φ::SyntaxTree)::AbstractVector{<:SyntaxToken}`
  * `atoms(φ::SyntaxTree)::AbstractVector{<:AbstractAtom}`
  * `truths(φ::SyntaxTree)::AbstractVector{<:Truth}`
  * `leaves(φ::SyntaxTree)::AbstractVector{<:SyntaxLeaf}`
  * `connectives(φ::SyntaxTree)::AbstractVector{<:Connective}`
  * `operators(φ::SyntaxTree)::AbstractVector{<:Operator}`
  * `ntokens(φ::SyntaxTree)::Int`
  * `natoms(φ::SyntaxTree)::Int`
  * `ntruths(φ::SyntaxTree)::Int`
  * `nleaves(φ::SyntaxTree)::Int`
  * `nconnectives(φ::SyntaxTree)::Int`
  * `noperators(φ::SyntaxTree)::Int`
  * `tokenstype(φ::SyntaxTree)`
  * `atomstype(φ::SyntaxTree)`
  * `truthstype(φ::SyntaxTree)`
  * `leavestype(φ::SyntaxTree)`
  * `connectivestype(φ::SyntaxTree)`
  * `operatorstype(φ::SyntaxTree)`
  * `composeformulas(c::Connective, φs::NTuple{N,SyntaxTree})`

さらに[`SyntaxLeaf`](@ref)、[`SyntaxBranch`](@ref)、[`SyntaxStructure`](@ref)、[`Formula`](@ref)も参照してください。
