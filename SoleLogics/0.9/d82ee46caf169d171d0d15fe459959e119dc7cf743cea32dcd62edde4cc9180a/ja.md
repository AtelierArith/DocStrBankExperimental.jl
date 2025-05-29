```
precedence(c::Connective)
```

バイナリ接続詞の優先順位を返します。

中置表記を使用する場合、かつ括弧がない場合、`precedence`はバイナリ接続詞がどのように解釈されるかを決定します。優先順位の値は標準の整数であり、高い優先順位を持つ接続詞は低い優先順位の接続詞よりも優先されます。これは、数式がどのように表示されるか（`syntaxstring`を介して）や、どのように解析されるか（`parseformula`を介して）に影響します。

デフォルトでは、`NamedConnective`の値はそのシンボル（`name`）の`Base.operator_precedence`から導出されます。いくつかの例外があります（例：¬）。そのため、カスタム接続詞`⊙`を扱う場合、`parseformula("p ⊙ q ∧ r") == (@synexpr p ⊙ q ∧ r)`となります。

接続詞タイプ`C`に特定の優先順位を割り当てることは、`Base.operator_precedence(::C)`メソッドを提供することで可能です。

# 例

```julia-repl
julia> precedence(∧) == Base.operator_precedence(:∧)
true

julia> precedence(∧), precedence(∨), precedence(→)
∨(12, 11, 4)

julia> syntaxstring(parseformula("¬a ∧ b ∧ c"))
"¬a ∧ b ∧ c"

julia> syntaxstring(parseformula("¬a → b ∧ c"))
"(¬a) → (b ∧ c)"

julia> syntaxstring(parseformula("a ∧ b → c ∧ d"))
"(a ∧ b) → (c ∧ d)"
```

[`associativity`](@ref)や[`Connective`](@ref)も参照してください。
