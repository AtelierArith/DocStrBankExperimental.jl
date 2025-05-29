```
is_principal_fac_elem(A::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, FacElem{AbsSimpleNumFieldElem, number_field}
```

$$
A
$$

が主イデアルであるかをテストし、$A = \langle \alpha\rangle$の場合は$(\mathtt{true}, \alpha)$を、そうでない場合は$(\mathtt{false}, 1)$を返します。生成元は因子形式で表されます。
