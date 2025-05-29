```
SimplicialComplex{T}
```

型 `T` の頂点を持つ抽象単体複体を、ファセットのリストを格納することで保存します。

# コンストラクタ

```
SimplicialComplex(itr, [vertices=union(itr...)])
```

`itr` の最大要素をファセットとして使用します。オプションの引数 `vertices` は、いくつかの頂点が面として現れない場合に頂点集合を指定できます。頂点は型 `eltype(vertices)` であり、`vertices` が空の場合は型 `TheIntegerType` が使用されます。このコンストラクタは、[グレード付き逆辞書順](https://en.wikipedia.org/wiki/Monomial_order#Graded_reverse_lexicographic_order) に従って `itr` の要素をソートします。詳細は [`lessequal_GrRevLex`](@ref) を参照してください。

```
SimplicialComplex(B; order="rows")
```

バイナリ行列 `B` の行をコードワードとして解釈します。`order="cols"` の場合は、最初に `B` を転置します。デフォルトでは、頂点に `TheIntegerType` を使用しますが、必要に応じてより大きな `Int` 型を使用します（`B` が *本当に* 大きい場合）。
