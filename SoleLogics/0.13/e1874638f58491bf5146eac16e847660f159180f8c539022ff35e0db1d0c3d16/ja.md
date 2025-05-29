```
normalize(
    f::Formula;
    profile = :readability,
    remove_boxes = nothing,
    reduce_negations = true,
    simplify_constants = true,
    allow_atom_flipping = false,
    prefer_implications = false,
    remove_implications = false,
    forced_negation_removal = nothing,
    remove_identities = true,
    unify_toones = true,
    rotate_commutatives = true,
    flip_atom = nothing,
)
```

与えられた式の修正されたバージョンを返します。これは同じ意味を持ちますが、異なる構文を持ちます。これは、可読性のために式を簡素化したり、（おそらく意味的に類似した）多くの式の真偽を確認する際に便利です。たとえば、[モデル検査](https://en.wikipedia.org/wiki/Model_checking)を行うときなどです。現在の実装は、基礎となる代数がブール代数であると仮定しています！

# 引数

  * `f::Formula`: `true`に設定された場合、式;
  * `profile::Symbol`: 可能な値は:readabilityであり、人間が理解するための質的な単純さを最適化し、:modelcheckingであり、モデル検査の速度を最適化します;
  * `remove_boxes::Bool`: 同等性◊φ ≡ ¬□¬φを使用して、すべての（非関係的および関係的）ボックス演算子を削除します。注意：これは基礎となるブール代数を仮定しています。
  * `reduce_negations::Bool`: `true`に設定された場合、いくつかの変換ルールを適用することによって否定の数を減らそうとします（例：[ド・モルガンの法則](https://en.wikipedia.org/wiki/De_Morgan%27s_laws)）。注意：これは基礎となるブール代数を仮定しています。
  * `allow_atom_flipping::Bool`: `true`に設定された場合、`reduce_negations=true`とともに、原子の否定がその[`dual`](@ref)原子に置き換えられる可能性があります。
  * `flip_atom::Union{Nothing,Callable}`: 呼び出し可能なものが提供されると、それは原子を反転させるかどうかを決定するために使用されます。

# 例

```julia-repl
julia> f = parseformula("□¬((p∧¬q)→r)∧⊤");

julia> syntaxstring(f)
"□¬((p ∧ ¬q) → r) ∧ ⊤"

julia> syntaxstring(SoleLogics.normalize(f; profile = :modelchecking, allow_atom_flipping = false))
"¬◊(q ∨ ¬p ∨ r)"

julia> syntaxstring(SoleLogics.normalize(f; profile = :readability, allow_atom_flipping = false))
"□(¬r ∧ p ∧ ¬q)"
```

さらに[`SyntaxTree`](@ref)、[`Formula`](@ref)を参照してください。
