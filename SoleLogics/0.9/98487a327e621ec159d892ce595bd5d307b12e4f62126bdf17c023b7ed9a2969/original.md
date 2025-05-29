```
modallogic(;
    alphabet = AlphabetOfAny{String}(),
    operators = [⊤, ⊥, ¬, ∧, ∨, →, ◊, □],
    grammar = CompleteFlatGrammar(AlphabetOfAny{String}(), [⊤, ⊥, ¬, ∧, ∨, →, ◊, □]),
    algebra = BooleanAlgebra(),
)
```

Instantiate a [modal logic](https://simple.wikipedia.org/wiki/Modal_logic) given a grammar and an algebra. Alternatively, an alphabet and a set of operators can be specified instead of the grammar.

# Examples

```julia-repl
julia> (¬) isa operatorstype(modallogic());
true

julia> (□) isa operatorstype(modallogic());
true

julia> (□) isa operatorstype(modallogic(; operators = [¬, ∨]))
┌ Warning: Instantiating modal logic (via `modallogic`) with solely propositional operators (SoleLogics.NamedConnective[¬, ∨]). Consider using propositionallogic instead.
└ @ SoleLogics ~/.julia/dev/SoleLogics/src/modal-logic.jl:642
false

julia> modallogic(; alphabet = ["p", "q"]);

julia> modallogic(; alphabet = ExplicitAlphabet([Atom("p"), Atom("q")]));

```

See also [`propositionallogic`](@ref), [`AbstractAlphabet`](@ref), [`AbstractAlgebra`](@ref).
