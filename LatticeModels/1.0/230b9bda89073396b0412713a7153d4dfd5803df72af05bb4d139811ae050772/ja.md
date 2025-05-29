```
span_unitcells([f, ]unitcell, dims...[; boundaries, offset])
```

`unitcell`を`dims`次元にわたってスパンすることでブラヴァイ格子を構築し、`f`でフィルタリングします。

## 引数

  * `f`: サイトが格子に含まれるかどうかを定義する関数。`BravaisSite`を受け取り、`Bool`を返します。
  * `unitcell`: `UnitCell`オブジェクト。
  * `dims`: 各次元における格子のサイズを指定する`Integer`または`Range`のリスト。

## キーワード引数

  * `default_translations`: 格子にデフォルトの境界条件軸として追加する`BravaisTranslation`のリスト。
  * `boundaries`: 格子の境界条件を指定する`BoundaryConditions`オブジェクト。
  * `rmdup`: 境界条件を適用した後に同等のサイトを削除するかどうかを指定する`Bool`。
  * `offset`: 原点からの格子のオフセット。詳細は`UnitCell`を参照してください。
  * `rotate`: 格子に適用する回転行列。詳細は`UnitCell`を参照してください。

オフセットと回転は、格子がスパンされる前にユニットセルに適用されることに注意してください（`f`が適用される前）。格子がスパンされた後に適用するには、`postoffset`および`postrotate`キーワードを使用してください。

## 例

```jldoctest
julia> using LatticeModels

julia> using LatticeModels

julia> uc = UnitCell([[1, 0] [0, 1]])
1-site Unit cell of a 2-dim Bravais lattice in 2D space:
  Basis site coordinates:
    ⎡ 0.000⎤
    ⎣ 0.000⎦
  Translation vectors:
    ⎡ 1.000⎤  ⎡ 0.000⎤
    ⎣ 0.000⎦  ⎣ 1.000⎦

julia> span_unitcells(uc, 3, 3) == SquareLattice(3, 3)
true
```
