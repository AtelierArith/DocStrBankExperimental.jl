```
sunit_mod_units_group_fac_elem(I::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> GrpAb, Map
```

配列 $I$ の (互いに素な素) 理想に対して、$I$ によって定義される $S$-ユニット群を見つけます。すなわち、フィールドの単位で割り算されることなく、$I$ の理想によってのみ割り算される非ゼロフィールド要素の群です。このマップは、因数分解された形で要素を返します。
