```
struct LeftmostLinearForm{C<:Connective,SS<:SyntaxStructure} <: SyntaxStructure
    grandchildren::Vector{<:SS}
end
```

他の構文構造 `SS` の集合の [`foldl`](https://en.wikipedia.org/wiki/Fold_(higher-order_function)) を接続詞 `C` によって表す構文構造。この構造は、論理和/論理積の形での式の構造化されたインスタンス化を可能にし、論理積標準形 (CNF) または論理和標準形 (DNF) を次のように定義します。

```
const LeftmostConjunctiveForm{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∧),SS}
const LeftmostDisjunctiveForm{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∨),SS}

const CNF{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∧),LeftmostLinearForm{typeof(∨),SS}}
const DNF{SS<:SyntaxStructure} = LeftmostLinearForm{typeof(∨),LeftmostLinearForm{typeof(∧),SS}}
```

# 例

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
LeftmostConjunctiveForm with 2 Atom{String} grandchildren:
        p
        q

julia> tree(conj)
SyntaxBranch: p ∧ q

julia> nconj = NEGATION(conj)
LeftmostLinearForm with connective ¬ and 1 LeftmostConjunctiveForm{Atom{String}} grandchildren:
        (p) ∧ (q)

julia> tree(nconj)
SyntaxBranch: ¬(p ∧ q)

julia> tree(nconj ∧ nconj)
SyntaxBranch: ¬(p ∧ q) ∧ ¬(p ∧ q)
```

[`SyntaxStructure`](@ref)、[`SyntaxTree`](@ref)、[`LeftmostConjunctiveForm`](@ref)、[`LeftmostDisjunctiveForm`](@ref)、[`Literal`](@ref) も参照してください。
