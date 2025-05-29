```
is_principal_with_data(A::AbsSimpleNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldOrderElem
is_principal_with_data(A::AbsSimpleNumFieldOrderFractionalIdeal) -> Bool, AbsSimpleNumFieldElem
```

$$
A
$$

が主イデアルであるかをテストし、$A = \langle \alpha\rangle$ の場合は $(\mathtt{true}, \alpha)$ を、そうでない場合は $(\mathtt{false}, 1)$ を返します。
