## StructuralElement

抽象構造要素タイプ。

### タイプ

```julia
abstract type StructuralElement end
```

### サブタイプ

```julia
* Rod::StructuralElement          : Rod(nxe, np_types, nip, fin_el)
* Beam::StructuralElement         : Beam(nod, nodof)
* Frame::StructuralElement        : Frame(nod, nodof)
* Plane::StructuralElement        : Plane(nod, nodof)
* Solid::StructuralElement        : Solid(nod, nodof)
* GenericSolid::StructuralElement : GenericSolid(nod, nodof)
```

### 関連ヘルプ

```julia
?FiniteElement                    : すべての有限要素を表示
?Rod                              : Rod構造要素に関するヘルプ
?Beam                             : Beam構造要素に関するヘルプ
?Frame                            : Frame構造要素に関するヘルプ
?Plane                            : Plane構造要素に関するヘルプ
?Solid                            : Solid構造要素に関するヘルプ
?GenericSolid                     : GenericSolid構造要素に関するヘルプ
```
