```
frobenius(x::FqPolyRepFieldElem, n = 1)
```

有限体の特性 $p$ において、要素 $a$ を $a^p$ に送るフロベニウス写像 $\sigma_p$ に対して、反復フロベニウス $\sigma_p^n(x)$ を返します。デフォルトでは、$n$ が指定されていない場合、フロベニウス写像は $n = 1$ 回適用されます。
