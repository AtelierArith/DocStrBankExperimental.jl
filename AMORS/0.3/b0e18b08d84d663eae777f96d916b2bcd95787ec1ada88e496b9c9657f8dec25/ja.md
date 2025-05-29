```
info.η
AMORS.effective_hyperparameter(info::AMORS.Info)
AMORS.effective_hyperparameter(μ, q, ν, r)
```

はAMORSアルゴリズムにおける効果的ハイパーパラメータの値を返します：

```
η = ((r/q)^qp + (q/r)^rp)*(μ^rp)*(ν^qp)
```

ここで：

```
qp = q/(q + r)
rp = r/(q + r)
```

`q = deg(J)`および`r = deg(K)`は関数`J(x)`および`K(y)`の同次次数であり、`μ > 0`および`ν > 0`はそれぞれの乗数です。必要なすべての引数はAMORSアルゴリズムの状態`info`によって提供される場合があります。
