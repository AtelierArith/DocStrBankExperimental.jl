```
setup_well(D::DataDomain, reservoir_cells; skin = 0.0, Kh = nothing, radius = 0.1, dir = :z, name = :Well)
w = setup_well(D, 1, name = :MyWell)         # グリッド内のセル 1
w = setup_well(D, (2, 5, 1), name = :MyWell) # 論理的に構造化されたメッシュ内の位置 (2, 5, 1)
w2 = setup_well(D, [1, 2, 3], name = :MyOtherWell)
```

`reservoir_cells` に与えられたスキンファクターと半径で井戸を設定します。セルの順序は重要であり、軌跡として扱われます。

`name` キーワード引数は、モデルに単一の井戸（`:Well`という名前）がある場合はデフォルトのままにできます。井戸を設定する際には、これを提供することを強くお勧めします。

`reservoir_cells` は次のいずれかである必要があります: セルのベクター、単一のセル、`(I, J, K)` タプルのベクター、または同じタイプの単一のタプル。
