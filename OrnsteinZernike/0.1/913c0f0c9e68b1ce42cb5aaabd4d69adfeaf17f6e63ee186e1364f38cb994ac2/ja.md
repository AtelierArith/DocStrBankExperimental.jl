```
CustomPotential
```

ユーザー定義関数を評価するポテンシャルを実装します。

呼び出し可能な値 `f` とパラメータのリスト `p` を期待します。関数は `f(r::Number, p)` と呼ばれ、単一成分システムの場合は `Number` を、複数成分システムの場合は `SMatrix` を生成する必要があります。

例:

```julia
f = (r, p) -> 4*p[1]*((p[2]/r)^12 -  (p[2]/r)^6)
potential = CustomPotential(f, (1.0, 1.0))
```
