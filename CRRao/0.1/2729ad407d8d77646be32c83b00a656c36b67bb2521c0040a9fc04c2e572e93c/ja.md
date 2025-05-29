```julia
ポアソン回帰
```

ポアソン回帰モデルクラスを表す型。

$$
y_i \sim Poisson(\lambda_i), i=1,2,\cdots,n
$$

ここで

$$
\lambda_i = \exp(\alpha +\mathbf{x}_i^T\beta),
$$

  * $$
    y_i
    $$

    は応答ベクトル $y$ の $i^{th}$ 要素、
  * $$
    \mathbf{x}=(x_{i1},x_{i2},\cdots,x_{in})
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
