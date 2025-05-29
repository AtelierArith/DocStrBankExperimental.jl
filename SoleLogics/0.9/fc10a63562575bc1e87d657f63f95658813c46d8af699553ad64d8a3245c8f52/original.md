```
syntaxstring(s::Syntactical; kwargs...)::String
```

Return the string representation of any syntactic object (e.g., `Formula`, `SyntaxTree`, `SyntaxToken`, `Atom`, `Truth`, etc). Note that this representation may introduce redundant parentheses. `kwargs` can be used to specify how to display syntax tokens/trees under some specific conditions.

The following `kwargs` are currently supported:

  * `function_notation = false::Bool`: when set to `true`, it forces the use of  function notation for binary operators  (see [here](https://en.wikipedia.org/wiki/Infix_notation)).
  * `remove_redundant_parentheses = true::Bool`: when set to `false`, it prints a syntaxstring  where each syntactical element is wrapped in parentheses.
  * `parenthesize_atoms = !remove_redundant_parentheses::Bool`: when set to `true`,  it forces the atoms (which are the leaves of a formula's tree structure) to be  wrapped in parentheses.

# Examples

```julia-repl
julia> syntaxstring(parseformula("p∧q∧r∧s∧t"))
"p ∧ q ∧ r ∧ s ∧ t"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), function_notation=true)
"∧(∧(∧(∧(p, q), r), s), t)"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), remove_redundant_parentheses=false)
"((((p) ∧ (q)) ∧ (r)) ∧ (s)) ∧ (t)"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), remove_redundant_parentheses=true, parenthesize_atoms=true)
"(p) ∧ (q) ∧ (r) ∧ (s) ∧ (t)"

julia> syntaxstring(parseformula("◊((p∧s)→q)"))
"◊((p ∧ s) → q)"

julia> syntaxstring(parseformula("◊((p∧s)→q)"); function_notation = true)
"◊(→(∧(p, s), q))"
```

See also [`parseformula`](@ref), [`SyntaxBranch`](@ref), [`SyntaxToken`](@ref).

# Implementation

In the case of a syntax tree, `syntaxstring` is a recursive function that calls itself on the syntax children of each node. For a correct functioning, the `syntaxstring` must be defined (including the `kwargs...` part!) for every newly defined `SyntaxToken` (e.g., `SyntaxLeaf`s, that is, `Atom`s and `Truth` values, and `Operator`s), in a way that it produces a *unique* string representation, since `Base.hash` and `Base.isequal`, at least for `SyntaxTree`s, rely on it.

In particular, for the case of `Atom`s, the function calls itself on the wrapped value:

```
syntaxstring(a::Atom; kwargs...) = syntaxstring(value(a); kwargs...)
```

The `syntaxstring` for any value defaults to its `string` representation, but it can be defined by defining the appropriate `syntaxstring` method.

!!! warning
    The `syntaxstring` for syntax tokens (e.g., atoms, operators) should not be prefixed/suffixed by whitespaces, as this may cause ambiguities upon *parsing*. For similar reasons, `syntaxstring`s should not contain parentheses (`'('`, `')'`), and, when parsing in function notation, commas (`','`).


See also [`SyntaxLeaf`](@ref), [`Operator`](@ref), [`parseformula`](@ref).
