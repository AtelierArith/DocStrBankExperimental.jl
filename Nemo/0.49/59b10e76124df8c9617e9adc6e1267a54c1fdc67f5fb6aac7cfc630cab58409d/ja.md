```
roots(x::AcbPolyRingElem; target=0, isolate_real=false, initial_prec=0, max_prec=0, max_iter=0)
```

複素多項式 $x$ の複素根を、含まれる球を反復的に洗練させることによって孤立させることを試みます。

これは、`initial_prec` から始めて作業精度を高めることによって行われます。最大反復回数は `max_iter` を使用して設定でき、最大精度は `max_prec` を使用して設定できます。

`isolate_real` が設定されていて $x$ が厳密に実数の場合、実根は非実根から孤立されます。すべての根はゼロ、正または負の実部を持ちます。

$$
x
$$

は平方自由であると仮定されます。
