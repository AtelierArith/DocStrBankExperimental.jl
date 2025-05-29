```
RBF{IT<:Integer , FT<:AbstractFloat} <: LinearBasisFunction
```

屋顶基函数 (Rooftop basis function, RBF) 基函数复合类型：

```
isbd        ::Bool              是否为边界元即半基函数，布尔类型
bfID        ::IT                基函数编号，整形
inGeo       ::MVector{2, IT}    基函数所在两个六面体编号（半基函数为1个，赋值成一样的两个），长度为2的向量数组
inGeoID     ::MVector{2, IT}    基函数在两个六面体中的局部编号（半基函数为1个，赋值成一样的两个），取值1:4，长度为2的向量数组
center      ::MVec3D{FT}        基函数中心，用于八叉树分组
```
