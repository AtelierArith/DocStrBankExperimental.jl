```
Transformation(el1, el2, residue_selectors...)
Transformation(coords1, coords2)
Transformation(trans1, trans2, rot)
```

1つの座標セットを別の座標セットにマッピングするための3D変換で、Kabschアルゴリズムを使用して見つけられます。

構造要素で呼び出されると、ペアワイズアライメントを実行し、整列した残基の原子に重ね合わせます。この場合、BioSequences.jlおよびBioAlignments.jlパッケージをインポートする必要があります。ペアワイズアライメントのためのキーワード引数を指定できます。残基セレクタは、ペアワイズアライメントを行う残基を決定します。キーワード引数`alignatoms`は、重ね合わせを計算する原子を選択する原子セレクタです（デフォルトは`calphaselector`）。同じサイズの2つの座標セットでも呼び出すことができ、最初の軸の次元数と2番目の軸のポイント数を持ちます。

返される`Transformation`オブジェクトは、最初のセットの平均座標、2番目のセットの平均座標、最初の中心化されたセットを2番目の中心化されたセットにマッピングするための回転、および関連する場合は最初と2番目の要素の整列した残基のインデックスで構成されています。
