```
abstract type Formula <: Syntactical end
```

論理式のための抽象型。`Formula`の例には、`SyntaxLeaf`（例えば、`Atom`や`Truth`値）、`SyntaxStructure`（例えば、`SyntaxTree`や`LeftmostLinearForm`）および`TruthTable`（構文構造に追加の[メモ化](https://en.wikipedia.org/wiki/Memoization)構造を関連付け、[モデル検査](https://en.wikipedia.org/wiki/Model_checking)時に計算時間を節約できる強化された表現）が含まれます。

任意の式は、[`tree`](@ref)を介してその[`SyntaxTree`](@ref)表現に変換でき、その[`height`](@ref)を計算でき、構文[`tokens`](@ref)、[`atoms`](@ref)などを照会できます... それは、[`syntaxstring`](@ref)表現から[`parseformula`](@ref)を介して解析できます。

# インターフェース

  * `tree(φ::Formula)::SyntaxTree`
  * `composeformulas(c::Connective, φs::NTuple{N,F})::F where {N,F<:Formula}`
  * さらに[`Syntactical`](@ref)も参照してください

# ユーティリティ関数（ツリーのウォークを必要とする）

  * `Base.in(tok::SyntaxToken, φ::Formula)::Bool`
  * `height(φ::Formula)::Int`
  * `tokens(φ::Formula)::AbstractVector{<:SyntaxToken}`
  * `atoms(φ::Formula)::AbstractVector{<:AbstractAtom}`
  * `truths(φ::Formula)::AbstractVector{<:Truth}`
  * `leaves(φ::Formula)::AbstractVector{<:SyntaxLeaf}`
  * `connectives(φ::Formula)::AbstractVector{<:Connective}`
  * `operators(φ::Formula)::AbstractVector{<:Operator}`
  * `ntokens(φ::Formula)::Int`
  * `natoms(φ::Formula)::Int`
  * `ntruths(φ::Formula)::Int`
  * `nleaves(φ::Formula)::Int`
  * `nconnectives(φ::Formula)::Int`
  * `noperators(φ::Formula)::Int`

さらに[`tree`](@ref)、[`SyntaxStructure`](@ref)、[`SyntaxLeaf`](@ref)も参照してください。
