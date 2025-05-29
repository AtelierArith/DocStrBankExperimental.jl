```
EmpiricalCopula{M}
```

フィールド:

```
-data::M - 2xn 行列の観測値
```

コンストラクタ

```
EmpiricalCopula(data)
```

$$
(x_k, y_k), k = 1,2, \ldots, n
$$

を連続二変量分布からのサイズ $n$ のサンプルとします。エンピリカルコピュラは次の関数です。

$$
C_n(\frac{i}{n},\frac{j}{n}) = \frac{\text{サンプル内のペア (x,y) の数で} x \leq x_{(i)}, y \leq y_{(j)} }{n}
$$

詳細については、以下を参照してください。

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
