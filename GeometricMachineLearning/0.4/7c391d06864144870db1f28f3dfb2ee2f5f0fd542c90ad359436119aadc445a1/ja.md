```
PSDLayer(input_dim, output_dim)
```

`PSDLayer`のインスタンスを作成します。

これは、シンプレクティックオートエンコーダー用のPSDのような層です。1つの層は次の形状を持ちます：

$$
A = \begin{bmatrix} \Phi & \mathbb{O} \\ \mathbb{O} & \Phi \end{bmatrix},
$$

ここで、$\Phi$はStiefel多様体$St(n, N)$の要素です。
