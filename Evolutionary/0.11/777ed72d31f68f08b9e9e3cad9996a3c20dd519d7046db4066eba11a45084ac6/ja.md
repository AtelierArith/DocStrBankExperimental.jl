```
cauchy(x, s::IsotropicStrategy)
```

与えられた戦略 `s` に基づいて、再組み換えされた `x` の等方的変異を行います。これは、次のようにコーシー分布からのノイズを加えることによって行われます：

  * $$
    x_i^\prime = x_i + s.\sigma_i \delta_i
    $$

ここで、$\delta$ はスケールパラメータ $t = 1$ のコーシー乱数変数です [^2]。
