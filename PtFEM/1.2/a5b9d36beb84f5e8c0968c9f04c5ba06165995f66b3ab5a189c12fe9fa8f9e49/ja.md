## フレーム

ピンまたは剛接合された構造要素。

### コンストラクタ

```julia
Frame(nels, nn, ndim, finite_element(nod, nodof))
```

### 引数

```julia
* nels::Int             : 要素の数
* nn:Int                : ノードの数
* ndim::Int             : 次元の数
* nst::Int              : 応力項の数
* nip::Int              : 積分点の数
* fin_el::FiniteElement : 線分(nod, nodof)
```

### 関連ヘルプ

```julia
?StructuralElement  : 構造要素のリスト
?FiniteElement      : 有限要素タイプのリスト
?Line               : 線分有限要素に関するヘルプ
```
