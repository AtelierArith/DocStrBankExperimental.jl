## ロッド

軸方向の応力のみを持つコンクリート1D構造要素。

### コンストラクタ

```julia
Rod(nels, np_types, nip, fin_el)
```

### 引数

```julia
* nels::Int             : fin_elsの数（フィールドnxeに格納）
* np_types::Int         : 異なるプロパティタイプの数
* nip::Int              : 積分点の数
* fin_el::FiniteElement : Line(nod, nodof)
```

### 関連ヘルプ

```julia
?StructuralElement      : 構造要素に関するヘルプ
?FiniteElement          : 有限要素タイプに関するヘルプ
?Line                   : Line有限要素に関するヘルプ
```
