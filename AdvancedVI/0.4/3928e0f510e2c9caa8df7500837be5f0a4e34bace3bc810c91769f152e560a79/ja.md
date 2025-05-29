```
PolynomialAveraging(eta)
```

ShamirとZhangによって提案された多項式平均化ルール[^SZ2013]。イテレーション`t`において、多項式平均化ルールに従ったパラメータ平均$ \bar{\lambda}_t :は次のように与えられます。

$$
    \bar{\lambda}_t = (1 - w_t) \bar{\lambda}_{t-1} + w_t \lambda_t \, ,
$$

ここで、平均化重みは次のように定義されます。

$$
    w_t = \frac{\eta + 1}{t + \eta} \, .
$$

より高い`eta`（$\eta$）は、初期のイテレーションの重みを下げます。$\eta=0$のとき、これはオンライン方式でイテレートを均等に平均化することに相当します。DoG論文[^IHC2023]は$\eta=8$を提案しています。

# パラメータ

  * `eta`: 正則化項。（デフォルト: `8`）

[^SZ2013]: Shamir, O., & Zhang, T. (2013). Stochastic gradient descent for non-smooth optimization: Convergence results and optimal averaging schemes. In International conference on machine learning (pp. 71-79). PMLR.
