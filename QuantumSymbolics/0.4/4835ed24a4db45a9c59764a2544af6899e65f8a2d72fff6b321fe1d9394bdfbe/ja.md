```
qsimplify(s; rewriter=nothing)
```

量子オブジェクトの象徴的な表現を手動で簡略化します。

キーワード `rewriter` が指定されていない場合、`qsimplify` は表現に対して定義されたすべてのルールを適用します。パフォーマンスや特定の目的のために、ユーザーは `qsimplify` が表現に適用する特定のリライターを定義するオプションがあります。簡略化のために定義されたリライターは以下のオブジェクトです：     - `qsimplify_pauli`     - `qsimplify_commutator`     - `qsimplify_anticommutator`     - `qsimplify_fock`

```jldoctest
julia> qsimplify(σʸ*commutator(σˣ*σᶻ, σᶻ))
(0 - 2im)Z

julia> qsimplify(anticommutator(σˣ, σˣ), rewriter=qsimplify_anticommutator)
2𝕀
```
