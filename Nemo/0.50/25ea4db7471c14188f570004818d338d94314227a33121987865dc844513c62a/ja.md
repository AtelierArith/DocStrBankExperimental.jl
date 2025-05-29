```
eigenvalues_simple(A::AcbMatrix, algorithm::Symbol = :default)
```

`A`の固有値を`AcbFieldElem`のベクトルとして返します。`A`が単純な固有値のみを持つと仮定されています。

使用するアルゴリズムは、`algorithm`キーワードを`:vdhoeven_mourrain`または`:rump`に設定することで変更できます。

この関数は実験的です。
