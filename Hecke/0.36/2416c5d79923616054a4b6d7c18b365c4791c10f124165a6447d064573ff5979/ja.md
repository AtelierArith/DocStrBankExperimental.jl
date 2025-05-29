```
is_principal_fac_elem(I::FacElem{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, AbsNumFieldOrderIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Bool, FacElem{AbsSimpleNumFieldElem, number_field}
```

$$
I
$$

が主であるかをテストし、$A = \langle \alpha\rangle$の場合は$(\mathtt{true}, \alpha)$を、そうでない場合は$(\mathtt{false}, 1)$を返します。生成元は因子形式になります。
