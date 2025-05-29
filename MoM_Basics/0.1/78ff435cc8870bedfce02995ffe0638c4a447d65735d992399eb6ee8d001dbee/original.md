```
RWG{IT<:Integer , FT<:AbstractFloat} <: LinearBasisFunction
```

RWG基函数复合类型：

```
isbd        ::Bool              是否为边界元即半基函数，布尔类型
bfID        ::IT                基函数编号，整形
edgel       ::FT                基函数边长，浮点型
inGeo       ::MVector{2, IT}    基函数所在两个三角形编号（半基函数为1个，赋值成一样的两个），长度为2的向量数组
inGeoID     ::MVector{2, IT}    基函数在两个上面三角形中的局部编号（半基函数为1个，赋值成一样的两个），取值1:3，长度为2的向量数组
center      ::MVec3D{FT}        基函数中心，用于八叉树分组
```
