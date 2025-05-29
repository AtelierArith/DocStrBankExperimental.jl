```
roots(x::ComplexPolyRingElem; target=0, isolate_real=false, initial_prec=0, max_prec=0, max_iter=0)
```

複素多項式 $x$ の複素根を隔離することを試み、根が存在する球を反復的に洗練します。

これは、`initial_prec` から始めて作業精度を上げることによって行われます。最大反復回数は `max_iter` を使用して設定でき、最大精度は `max_prec` を使用して設定できます。

`isolate_real` が設定されていて $x$ が厳密に実数の場合、実根は非実根から隔離されます。すべての根はゼロ、正または負の実部を持ちます。

$$
x
$$

は平方自由であると仮定されます。
