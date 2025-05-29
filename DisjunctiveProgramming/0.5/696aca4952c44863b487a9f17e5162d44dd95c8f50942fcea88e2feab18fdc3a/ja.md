```
@disjunctions(model, args...)
```

一度に複数の選言を追加します。これは `@disjunction` マクロと同様の方法です。

モデルは最初の引数でなければならず、複数の選言は `begin ... end` ブロック内に複数行で追加できます。

このマクロは、定義された選言を含むタプルを返します。

## 例

`julia model = GDPModel(); @variable(model, w); @variable(model, x); @variable(model, Y[1:4], LogicalVariable); @constraint(model, [i=1:2], w == i, Disjunct(Y[i])); @constraint(model, [i=3:4], x == i, Disjunct(Y[i])); @disjunctions(model, begin     [Y[1], Y[2]]     [Y[3], Y[4]] end);``
