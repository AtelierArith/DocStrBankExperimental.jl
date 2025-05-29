## ビーム

横方向およびモーメント荷重を持つコンクリート構造要素。

### コンストラクタ

```julia
Beam(ndim, nst, nxe, nip, direction, fin_el, axisymmetric)
```

### 引数

```julia
* ndim::Int             : 次元数
* nst::Int              : 応力項の数
* nxe::Int              : 異なる特性タイプの数
* nip::Int              : 積分点の数
* direction::Symbol     : 積分点の数
* fin_el::FiniteElement : 線分(nod, nodof)
* axisymmetric::Bool    : 真の場合は軸対称
```

### 関連ヘルプ

```julia
?StructuralElement      : 構造要素に関するヘルプ
?FiniteElement          : 有限要素タイプに関するヘルプ
?Line                   : 線分有限要素に関するヘルプ
```
