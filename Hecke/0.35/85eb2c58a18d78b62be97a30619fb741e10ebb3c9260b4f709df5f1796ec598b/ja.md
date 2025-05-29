```
is_power(A::AbsNumFieldOrderIdeal, n::Int) -> Bool, AbsNumFieldOrderIdeal
is_power(A::AbsSimpleNumFieldOrderFractionalIdeal, n::Int) -> Bool, AbsSimpleNumFieldOrderFractionalIdeal
```

理想 $B$ を計算します。$B^n==A$ が成り立つ場合、`true` と $B$ が返されます。
