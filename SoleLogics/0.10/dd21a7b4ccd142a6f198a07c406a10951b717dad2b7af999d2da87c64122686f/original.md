```
struct LeftmostLinearForm{C<:Connective,SS<:SyntaxStructure} <: SyntaxStructure
    children::Vector{<:SS}
end
```

A syntax structure representing the [`foldl`](https://en.wikipedia.org/wiki/Fold_(higher-order_function)) of a set of other syntax structure of type `SS` by means of a connective `C`. This structure enables a structured instantiation of formulas in conjuctive/disjunctive forms, and conjuctive normal form (CNF) or disjunctive normal form (DNF), defined as:

```
const LeftmostConjunctiveForm{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∧),SS}
const LeftmostDisjunctiveForm{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∨),SS}

const CNF{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∧),LeftmostLinearForm{typeof(∨),SS}}
const DNF{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∨),LeftmostLinearForm{typeof(∧),SS}}
```

# Examples

```julia-repl
julia> LeftmostLinearForm(→, parseformula.(["p", "q", "r"]))
LeftmostLinearForm{SoleLogics.NamedConnective{:→},Atom{String}}
    "(p) → (q) → (r)"

julia> LeftmostConjunctiveForm(parseformula.(["¬p", "q", "¬r"]))
LeftmostLinearForm{SoleLogics.NamedConnective{:∧},SyntaxTree}
    "(¬p) ∧ (q) ∧ (¬r)"

julia> LeftmostDisjunctiveForm{Literal}([Literal(false, Atom("p")), Literal(true, Atom("q")), Literal(false, Atom("r"))])
LeftmostLinearForm{SoleLogics.NamedConnective{:∨},Literal}
    "(¬p) ∨ (q) ∨ (¬r)"

julia> LeftmostDisjunctiveForm([LeftmostConjunctiveForm(parseformula.(["¬p", "q", "¬r"]))]) isa DNF
true

julia> conj = LeftmostConjunctiveForm(@atoms p q)
LeftmostConjunctiveForm with 2 Atom{String} children:
        p
        q

julia> tree(conj)
SyntaxBranch: p ∧ q

julia> nconj = NEGATION(conj)
LeftmostLinearForm with connective ¬ and 1 LeftmostConjunctiveForm{Atom{String}} children:
        (p) ∧ (q)

julia> tree(nconj)
SyntaxBranch: ¬(p ∧ q)

julia> tree(nconj ∧ nconj)
SyntaxBranch: ¬(p ∧ q) ∧ ¬(p ∧ q)
```

See also [`SyntaxStructure`](@ref), [`SyntaxTree`](@ref), [`LeftmostConjunctiveForm`](@ref), [`LeftmostDisjunctiveForm`](@ref), [`Literal`](@ref).
