```
precedence(c::Connective)
```

Return the precedence of a binary connective.

When using infix notation, and in the absence of parentheses, `precedence` establishes how binary connectives are interpreted. A precedence value is a standard integer, and connectives with high precedence take precedence over connectives with lower precedences. This affects how formulas are shown (via `syntaxstring`) and parsed (via `parseformula`).

By default, the value for a `NamedConnective` is derived from the `Base.operator_precedence` of its symbol (`name`); there are some exceptions (e.g., ¬). Because of this, when dealing with a custom connective `⊙`, it will be the case that `parseformula("p ⊙ q ∧ r") == (@synexpr p ⊙ q ∧ r)`.

It is possible to assign a specific precedence to a connective type `C` by providing a method `Base.operator_precedence(::C)`.

# Examples

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

See also [`associativity`](@ref), [`Connective`](@ref).
