```julia
LogisticRegression
```

ロジスティック回帰モデルクラスを表す型。

$$
y_i \sim Bernoulli(p_i), 
$$

ここで $i=1,2,\cdots,n, 0 < p_i < 1$、

  * $$
    \mathbb{E}(y_i)=p_i
    $$

    、
  * $$
    \mathbb{P}(y_i=1) = p_i
    $$

    および $\mathbb{P}(y_i=0) = 1-p_i$、したがって

$$
\mathbb{E}(y_i)= p_i =g(\alpha +\mathbf{x}_i^T\beta),
$$

  * $$
    g(.)
    $$

    はリンク関数、
  * $$
    y_i
    $$

    は応答ベクトル $y$ の $i^{th}$ 要素、
  * $$
    \mathbf{x}_i=(x_{i1},x_{i2},\cdots,x_{in})
    $$

    はサイズ $n \times p$ のデザイン行列の $i^{th}$ 行、
  * $$
    \alpha
    $$

    はモデルの切片、そして
  * $$
    \beta
    $$

    はモデルの回帰係数です。
