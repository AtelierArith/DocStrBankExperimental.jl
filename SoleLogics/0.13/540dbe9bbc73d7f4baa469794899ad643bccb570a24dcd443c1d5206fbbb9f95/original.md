```
associativity(::Connective)
```

Return whether a (binary) connective is right-associative.

When using infix notation, and in the absence of parentheses, `associativity establishes how binary connectives of the same`precedence`are interpreted. This affects how formulas are shown (via`syntaxstring`) and parsed (via`parseformula`).

By default, the value for a `NamedConnective` is derived from the `Base.operator_precedence` of its symbol (`name`); thus, for example, most connectives are left-associative (e.g., `∧` and `∨`), while `→` is right-associative. Because of this, when dealing with a custom connective `⊙`, it will be the case that `parseformula("p ⊙ q ∧ r") == (@synexpr p ⊙ q ∧ r)`.

# Examples

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

See also [`Connective`](@ref), [`parseformula`](@ref), [`precedence`](@ref), [`syntaxstring`](@ref).
