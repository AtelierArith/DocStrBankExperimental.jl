```
QQField <: FracField{ZZRingElem}
QQFieldElem <: FracFieldElem{ZZRingElem}
```

有理数の体 $\mathbb Q$ とその要素。便利のために、グローバル変数 `const QQ = QQField()` を事前に定義します。

# 例

```jldoctest
julia> QQ(2//3) == ZZ(2)//ZZ(3)
true

julia> QQ(1//6) - QQ(1//7)
1//42
```
