```
symeval(expr::Any)
```

`expr`をSymata評価シーケンスに通します。`expr`は`Mxpr`または数、シンボルなどです。

特に、`Expr`（すなわちSymataに翻訳されていないもの）は、Symata評価シーケンスによってSymata評価され（この場合、変更されずに返されることを意味します）。
