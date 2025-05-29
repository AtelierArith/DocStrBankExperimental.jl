## GenericSolid

固体構造要素。

### コンストラクタ

```julia
GenericSolid(ndim, nst, nels, nn, nip, finite_element(nod, nodof), axisymmetric)
```

### 引数

```julia
* ndim::Int               : 次元数
* nst::Int                : 応力項の数
* nels::Int               : 有限要素の数
* nn::Int                 : ノードの数
* nip::Int                : 積分点の数
* fin_el::FiniteElement   : 使用される有限要素のタイプ
* axisymmetric::Bool      : 軸対称
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素のリスト
?FiniteElement      : 有限要素タイプのリスト
```
