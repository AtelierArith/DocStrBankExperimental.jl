```
GradientLayerQ(n, upscaling_dimension, activation)
```

勾配-$q$ レイヤーのインスタンスを作成します。

$$
q
$$

成分を変更する勾配レイヤーです。形式は次の通りです：

$$
\begin{bmatrix}
        \mathbb{I} & \nabla{}V \\ \mathbb{O} & \mathbb{I} 
\end{bmatrix},
$$

ここで $V(p) = \sum_{i=1}^Ma_i\Sigma(\sum_jk_{ij}p_j+b_i)$ であり、$\mathtt{activation} \equiv \Sigma$ は活性化関数 $\sigma$ の不定積分（1層ニューラルネットワーク）です。$M$ を *アップスケーリング次元* と呼びます。

このようなレイヤーは構造上、シンプレクティックです。
