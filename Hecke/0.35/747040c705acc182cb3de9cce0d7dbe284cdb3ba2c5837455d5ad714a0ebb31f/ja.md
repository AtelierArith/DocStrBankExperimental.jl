```
sunit_group_fac_elem(I::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> GrpAb, Map
```

配列 $I$ の（互いに素な素数）イデアルに対して、$I$ によって定義される $S$-ユニット群を見つけます。つまり、$I$ のイデアルでのみ割り切れる非ゼロの体要素の群です。マップは要素を因子形式で返します。
