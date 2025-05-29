```
is_invertible(A::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldOrderFractionalIdeal
```

$$
A
$$

が可逆でない場合、`true`と$A$の逆元、または`false`と$A*B \subsetneq order(A)$を満たす理想$B$を返します。
