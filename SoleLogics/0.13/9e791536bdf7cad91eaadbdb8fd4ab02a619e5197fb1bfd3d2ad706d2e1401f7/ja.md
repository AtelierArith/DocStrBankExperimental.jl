```
propositionallogic(;
    alphabet = AlphabetOfAny{String}(),
    operators = SoleLogics.NamedConnective[¬, ∧, ∨, →],
    grammar = CompleteFlatGrammar(AlphabetOfAny{String}(), SoleLogics.NamedConnective[¬, ∧, ∨, →]),
    algebra = BooleanAlgebra()
)
```

文法と代数を指定して[命題論理](https://simple.wikipedia.org/wiki/Propositional_logic)をインスタンス化します。あるいは、文法の代わりにアルファベットと演算子のセットを指定することもできます。

# 例

```julia-repl
julia> (¬) isa operatorstype(propositionallogic())
true

julia> (¬) isa operatorstype(propositionallogic(; operators = [∨]))
false

julia> propositionallogic(; alphabet = ["p", "q"]);

julia> propositionallogic(; alphabet = ExplicitAlphabet([Atom("p"), Atom("q")]));

```

他にも[`modallogic`](@ref), [`AbstractAlphabet`](@ref), [`AbstractAlgebra`](@ref), [`AlphabetOfAny`](@ref), [`CompleteFlatGrammar`], [`BooleanAlgebra`](@ref), [`BASE_PROPOSITIONAL_CONNECTIVES`](@ref)を参照してください。
