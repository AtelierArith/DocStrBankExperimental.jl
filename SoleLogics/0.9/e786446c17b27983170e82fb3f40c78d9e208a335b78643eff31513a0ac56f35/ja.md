```
struct AnchoredFormula{L<:AbstractLogic} <: Formula
    _logic::Base.RefValue{L}
    synstruct::AbstractSyntaxStructure
end
```

`L`型の論理に固定された式であり、構文構造をラップしています。この構造は、論理の文法に属する式をエンコードしており、式の真偽は同じ論理の解釈に基づいて評価できます。ここで、論理は参照によって表されることに注意してください。

構築時に、論理は直接渡すことも、RefValueを介して渡すこともできます。さらに、以下のキーワード引数を指定することができます：

  * `check_atoms::Bool = false`: 原子が論理のアルファベットに属するかどうかをチェックするかどうか；
  * `check_tree::Bool = false`: 式の構文構造が文法を遵守しているかどうかをチェックするかどうか（`check_atoms = true`で行われるチェックを含む）；

*クールな機能*: `AnchoredFormula`は、同じ論理の他の式をインスタンス化するために使用できます。例を参照してください。

# 例

```julia-repl
julia> φ = parsebaseformula("◊(p→q)");

julia> f2 = φ(parseformula("p"));

julia> syntaxstring(φ)
"◊(→(p, q))"

julia> syntaxstring(f2)
"p"

julia> @assert logic(φ) == logic(f2)

julia> @assert ◊ in operators(logic(f2))

julia> @assert ◊ isa operatorstype(logic(f2))

```

[`AbstractLogic`](@ref)、[`logic`](@ref)、[`SyntaxToken`](@ref)、[`SyntaxBranch`](@ref)、[`tree`](@ref)も参照してください。
