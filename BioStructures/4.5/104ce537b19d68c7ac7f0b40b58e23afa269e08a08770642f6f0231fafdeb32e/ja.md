```
rmsd(element_one, element_two, residue_selectors...)
rmsd(element_one, element_two, superimpose=false)
rmsd(coords_one, coords_two)
```

2つの `StructuralElementOrList` または 2つの座標 `Array` の間のルート平均二乗偏差 (RMSD) を Å で取得します。

`superimpose` が `true` の場合（デフォルト）、要素はRMSD計算の前に重ね合わされ、RMSDは重ね合わされた残基に対して計算されます。この場合、BioSequences.jl および BioAlignments.jl パッケージをインポートする必要があります。キーワード引数については `Transformation` を参照してください。`superimpose` が `false` の場合、要素は重ね合わされていると見なされ、同じ長さでなければなりません。キーワード引数 `rmsdatoms` は、RMSDを計算するために選択する原子のセレクタであり（デフォルトは `calphaselector`）、です。
