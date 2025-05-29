```
@synexpr(expression)
```

未定義の [`Atom`](@ref) を自動的にインスタンス化した後に式を返します。

!!! info



すべての原子は `Atom{String}` オブジェクトとして解析されます。

!!! warning



Julia パーサーは ∧ や → のような一部の (中置) `NamedConnective` を解析できますが、いくつかの制限があります。これには以下が含まれます：

  * 一部の演算子に対する不正確な優先順位と結合性 (例：実際、Julia 1.9 の時点で、`(@synexpr ¬ p ∧ q) == @synexpr ¬(p) ∧ q` であるにもかかわらず、   Base.operator*precedence(:(¬)) < Base.operator*precedence(:(∧))) のように)；
  * ほとんどの多文字のカスタムメイド `Connective` (例：⟨=⟩, [G]) を解析できないこと；

より柔軟な解析を行うには、`parseformula` の使用を検討してください。

# 例

```julia-repl
julia> @synexpr x = p # Atom{String}("p") がグローバル変数 x に割り当てられます
Atom{String}("p")

julia> @synexpr st = p ∧ q → r
(p ∧ q) → r

julia> token(st)
→
```

他にも [`parseformula`](@ref)、[`Atom`](@ref)、[`Connective`](@ref)、[`precedence`](@ref)、[`associativity`](@ref) を参照してください。
