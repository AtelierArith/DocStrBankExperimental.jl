```
modallogic(;
    alphabet = AlphabetOfAny{String}(),
    operators = [⊤, ⊥, ¬, ∧, ∨, →, ◊, □],
    grammar = CompleteFlatGrammar(AlphabetOfAny{String}(), [⊤, ⊥, ¬, ∧, ∨, →, ◊, □]),
    algebra = BooleanAlgebra(),
)
```

文法と代数を指定して[モーダル論理](https://simple.wikipedia.org/wiki/Modal_logic)をインスタンス化します。あるいは、文法の代わりにアルファベットと演算子のセットを指定することもできます。

# 例

```julia-repl
julia> (¬) isa operatorstype(modallogic());
true

julia> (□) isa operatorstype(modallogic());
true

julia> (□) isa operatorstype(modallogic(; operators = [¬, ∨]))
┌ Warning: 述語演算子のみでモーダル論理をインスタンス化しています (SoleLogics.NamedConnective[¬, ∨]). propositionallogicの使用を検討してください。
└ @ SoleLogics ~/.julia/dev/SoleLogics/src/modal-logic.jl:642
false

julia> modallogic(; alphabet = ["p", "q"]);

julia> modallogic(; alphabet = ExplicitAlphabet([Atom("p"), Atom("q")]));

```

[`propositionallogic`](@ref)、[`AbstractAlphabet`](@ref)、[`AbstractAlgebra`](@ref)も参照してください。
