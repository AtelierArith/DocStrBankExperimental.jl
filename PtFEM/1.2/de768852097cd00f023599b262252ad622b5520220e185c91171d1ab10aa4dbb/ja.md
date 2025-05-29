## プレーン

プレート構造要素。

### コンストラクタ

```julia
Plane(ndim, nst, nxe, nye, nip, dir, finite_element(nod, nodof), axisymmetric)
```

### 引数

```julia
* ndim::Int               : 次元数
* nst::Int                : 応力項の数
* nxe::Int                : x方向の要素数
* nye::Int                : y方向の要素数
* nip::Int                : 積分点の数
* dir::Symbol             : ノード番号付けの方向
* fin_el::FiniteElement   : Line(nod, nodof)
* axisymmetric::Bool      : 軸対称
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素のリスト
?FiniteElement      : 有限要素タイプのリスト
?Line               : Line有限要素に関するヘルプ
```
