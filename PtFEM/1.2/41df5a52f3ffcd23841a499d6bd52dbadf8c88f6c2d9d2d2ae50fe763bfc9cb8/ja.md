## ソリッド

ソリッド構造要素。

### コンストラクタ

```julia
Solid(ndim, nst, nxe, nye, nze, nip, finite_element(nod, nodof))
```

### 引数

```julia
* ndim::Int             : 次元数
* nst::Int              : 応力項の数
* nxe::Int              : x方向の要素数
* nye::Int              : y方向の要素数
* nze::Int              : z方向の要素数
* nip::Int              : 積分点の数
* fin_el::FiniteElement : Line(nod, nodof)
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素のリスト
?FiniteElement      : 有限要素タイプのリスト
```
