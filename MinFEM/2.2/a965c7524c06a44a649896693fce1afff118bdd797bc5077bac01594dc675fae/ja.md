```
integral_over_reference_element(
    f::Function,
    d::Int64;
    order::Int64 = 1
) -> Float64
```

d次元FEM参照要素上の関数fの積分を返し、与えられた次数までの多項式に対して少なくとも正確なガウス・レジェンドル積分法で計算されます。
