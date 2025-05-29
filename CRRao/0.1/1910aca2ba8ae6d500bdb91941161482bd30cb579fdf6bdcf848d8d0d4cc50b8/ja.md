```julia
LinearRegression
```

線形回帰モデルクラスを表す型。

$$
y =\alpha +  X \beta+ \varepsilon,
$$

ここで 

$$
\varepsilon \sim N(0,\sigma^2),
$$

  * $$
    y
    $$

    はサイズ $n$ の応答ベクトル、
  * $$
    X
    $$

    はサイズ $n \times p$ の予測変数の行列、
  * $$
    n
    $$

    はサンプルサイズ、$p$ は予測変数の数、
  * $$
    \alpha
    $$

    はモデルの切片、
  * $$
    \beta
    $$

    はモデルの回帰係数、そして
  * $$
    \sigma
    $$

    はノイズ $\varepsilon$ の標準偏差です。
