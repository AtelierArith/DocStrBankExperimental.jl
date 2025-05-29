1. `AbstractModel`および`AbstractCost`インターフェースを実装する型を定義します。
2. オブジェクト`modelcost = ModelAndCost(model, cost)`を作成します。
3. マクロ`@define*modelcost*functions(modelcost)`を実行します。このマクロは以下の関数を定義します。

```
f(x, u, i)  = f(modelcost, x, u, i)
fT(x)       = fT(modelcost, x)
df(x, u, I) = df(modelcost, x, u, I)
```

`AbstractModel`、`AbstractCost`も参照してください。
