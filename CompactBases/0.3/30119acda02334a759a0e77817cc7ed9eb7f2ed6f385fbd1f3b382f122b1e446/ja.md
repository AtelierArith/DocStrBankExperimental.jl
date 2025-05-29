```
FunctionProduct{Conjugated}(L, R[, T; w=one]) where {Conjugated,T}
```

[`FunctionProduct`](@ref)を構築して、`L`と`R`それぞれに展開された2つの関数の積を計算します：

$$
h(x) = f^\circ(x)g(x)w(x)
$$

ここで、$w(x)$はオプションの重み関数であり、Vandermonde補間を介して$g(x)$の基底に対して定義されます。
