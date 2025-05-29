```
swinnerton_dyer(V::Vector, x::Generic.Poly{<:Generic.RationalFunctionFieldElem})
swinnerton_dyer(n::Int, x::Generic.Poly{<:Generic.RationalFunctionFieldElem})
```

$$
\sum \pm \sqrt{t+v_i}
$$

を$x$で評価したときの最小多項式を計算します。$t$は$x$の親の基底体の生成元です。

2番目の変種では、多項式は$\sum\pm\sqrt{t+i}$の根を持ち、$i=1,\ldots,n$です。
