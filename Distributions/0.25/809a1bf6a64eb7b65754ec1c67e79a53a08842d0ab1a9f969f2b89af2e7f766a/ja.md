[多項分布](http://en.wikipedia.org/wiki/Multinomial_distribution)は*二項分布*を一般化します。サイズkの有限集合に対するカテゴリカル分布からのn回の独立したサンプリングを考え、$X = (X_1, ..., X_k)$とし、ここで$X_i$は要素$i$が出現する回数を表すとき、$X$の分布は多項分布になります。多項分布の各サンプルは、合計がnになるk次元の整数ベクトルです。

確率質量関数は次のように与えられます。

$$
f(x; n, p) = \frac{n!}{x_1! \cdots x_k!} \prod_{i=1}^k p_i^{x_i},
\quad x_1 + \cdots + x_k = n
$$

```julia
Multinomial(n, p)   # n回の試行に対する確率ベクトルpの多項分布
Multinomial(n, k)   # 1:kの間で等しい確率のn回の試行に対する多項分布
```
