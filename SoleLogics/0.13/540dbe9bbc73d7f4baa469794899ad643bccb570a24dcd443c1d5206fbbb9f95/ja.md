```
associativity(::Connective)
```

バイナリ接続詞が右結合であるかどうかを返します。

中置記法を使用する場合、かつ括弧がない場合、`associativity`は同じ`precedence`のバイナリ接続詞がどのように解釈されるかを定めます。これは、数式がどのように表示されるか（`syntaxstring`を介して）や解析されるか（`parseformula`を介して）に影響します。

デフォルトでは、`NamedConnective`の値はそのシンボル（`name`）の`Base.operator_precedence`から導出されます。したがって、たとえば、ほとんどの接続詞は左結合（例：`∧`や`∨`）ですが、`→`は右結合です。このため、カスタム接続詞`⊙`を扱う場合、`parseformula("p ⊙ q ∧ r") == (@synexpr p ⊙ q ∧ r)`となります。

# 例

```julia-repl
julia> associativity(∧)
:left

julia> associativity(→)
:right

julia> syntaxstring(parseformula("p → q → r"); remove_redundant_parentheses = false)
"p → (q → r)"

julia> syntaxstring(parseformula("p ∧ q ∨ r"); remove_redundant_parentheses = false)
"(p ∧ q) ∨ r"
```

関連項目としては、[`Connective`](@ref)、[`parseformula`](@ref)、[`precedence`](@ref)、[`syntaxstring`](@ref)があります。
