```
@bravaisdef MyBravaisLattice UnitCell(...)
@bravaisdef MyBravaisLattice N -> UnitCell(...)

新しいブラヴァイ格子型 `MyBravaisLattice` を単位セルコンストラクタ `UnitCell(expr)` で定義します。表記が `N -> UnitCell(expr)` の場合、単位セルコンストラクタは次元性 `N` に依存します。それ以外の場合、次元性は単位セルから推測されます。`N` は格子の次元性です。

## 例

```

jldoctest julia> using LatticeModels

julia> @bravaisdef MyBravaisLattice UnitCell([1 0; 0 1]);   # 2D 正方格子

julia> MyBravaisLattice(3, 3) 9サイト 2次元 ブラヴァイ格子 2D空間内 単位セル:   基底サイト座標:     ⎡ 0.000⎤     ⎣ 0.000⎦   変換ベクトル:     ⎡ 1.000⎤  ⎡ 0.000⎤     ⎣ 0.000⎦  ⎣ 1.000⎦ 格子型: MyBravaisLattice デフォルトの変換:   :axis1 → Bravais[3, 0]   :axis2 → Bravais[0, 3] 最近接隣接ホッピング:   1.00000 =>     Bravais[1, 0]     Bravais[0, 1]   1.41421 =>     Bravais[1, -1]     Bravais[1, 1]   2.00000 =>     Bravais[2, 0]     Bravais[0, 2] 境界条件: なし ```
