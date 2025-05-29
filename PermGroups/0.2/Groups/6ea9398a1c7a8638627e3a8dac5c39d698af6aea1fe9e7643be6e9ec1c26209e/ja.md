このモジュールは群に関する基本的な機能を提供します。

`Group` は抽象型ですが、以下はその具体的な実装の1つである群 `G` に対して仮定されることです：

  * 関数 `gens(G)` は `G` の生成元のリストを返します。
  * 関数 `one(G)` は `G` の単位元を返します。

# 例

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3))
Group((1,2),(1,2,3))

julia> gens(G)
2-element Vector{Perm{Int16}}:
 (1,2)
 (1,2,3)

julia> ngens(G)
2

julia> minimal_words(G)
OrderedDict{Perm{Int16}, Vector{Int64}} with 6 entries:
  ()      => []
  (1,2)   => [1]
  (1,2,3) => [2]
  (1,3)   => [1, 2]
  (2,3)   => [2, 1]
  (1,3,2) => [2, 2]
```

任意の型の要素を持つ群のコンストラクタ `Group(l)` があり、ここで `l isa AbstractVector{T}` はこのモジュールの一般的なメソッドのみを知っている `Groupof{T}` を構築します。上記の例では、`Group(AbstractVector{<:Perm})` を使用しており、これはより効率的なメソッドを持つ `PermGroup` を構築します。

このモジュールで定義されている関数に関する詳細情報については、`Group, gens, ngens, comm, orbit, orbits, transversal, words_transversal, centralizer, stabilizer, center, normalizer, words, minimal_words, word, in, elements, length, order, conjugacy_class, conjugacy_classes, classreps, nconjugacy_classes, fusion_conjugacy_classes, position_class, isabelian, iscyclic, istrivial, rand, transporting_elt, intersect, Hom, kernel, Coset` のドキュメント文字列を参照してください。
