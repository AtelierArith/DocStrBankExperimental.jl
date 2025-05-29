```
propositionallogic(;
    alphabet = AlphabetOfAny{String}(),
    operators = SoleLogics.NamedConnective[¬, ∧, ∨, →],
    grammar = CompleteFlatGrammar(AlphabetOfAny{String}(), SoleLogics.NamedConnective[¬, ∧, ∨, →]),
    algebra = BooleanAlgebra()
)
```

Instantiate a [propositional logic](https://simple.wikipedia.org/wiki/Propositional_logic) given a grammar and an algebra. Alternatively, an alphabet and a set of operators can be specified instead of the grammar.

# Examples

```julia-repl
julia> (¬) isa operatorstype(propositionallogic())
true

julia> (¬) isa operatorstype(propositionallogic(; operators = [∨]))
false

julia> propositionallogic(; alphabet = ["p", "q"]);

julia> propositionallogic(; alphabet = ExplicitAlphabet([Atom("p"), Atom("q")]));

```

See also [`modallogic`](@ref),  [`AbstractAlphabet`](@ref), [`AbstractAlgebra`](@ref), [`AlphabetOfAny`](@ref), [`CompleteFlatGrammar`], [`BooleanAlgebra`](@ref), [`BASE_PROPOSITIONAL_CONNECTIVES`](@ref).
