```
displacements(element_one, element_two, residue_selectors...)
displacements(element_one, element_two, superimpose=false)
displacements(coords_one, coords_two)
```

2つの `StructuralElementOrList` または 2つの座標 `Array` から原子座標間のÅ単位の変位を取得します。

`superimpose` が `true` の場合（デフォルト）、要素は計算前に重ね合わされ、変位は重ね合わされた残基に対して計算されます。この場合、BioSequences.jl および BioAlignments.jl パッケージをインポートする必要があります。キーワード引数については `Transformation` を参照してください。`superimpose` が `false` の場合、要素は重ね合わされていると見なされ、同じ長さでなければなりません。キーワード引数 `dispatoms` は、変位を計算する原子を選択する原子セレクタです（デフォルトは `calphaselector`）。
