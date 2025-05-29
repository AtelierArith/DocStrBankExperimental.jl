```
GrassmannLieAlgHorMatrix(B::AbstractMatrix, N::Integer, n::Integer)
```

任意のサイズ $(N-n)\times{}n$ の行列 `B` に基づいて `GrassmannLieAlgHorMatrix` のインスタンスを構築します。

`GrassmannLieAlgHorMatrix` は *反対称行列のリー代数の水平成分* です（標準的なメトリックに関して）。

# 拡張ヘルプ

ここでの射影は次のようになります: $\pi:S \to SE/\sim$ ただし 

$$
E = \begin{bmatrix} \mathbb{I}_{n} \\ \mathbb{O}_{(N-n)\times{}n}  \end{bmatrix},
$$

および同値関係は 

$$
V_1 \sim V_2 \iff \exists A\in\mathcal{S}_\mathrm{skew}(n) \text{ そのとき } V_2 = V_1 + \begin{bmatrix} A \\ \mathbb{O} \end{bmatrix}
$$

`GrassmannLieAlgMatrix` の要素は次の形を取ります: 

$$
\begin{pmatrix}
\bar{\mathbb{O}} & B^T \\ B & \mathbb{O}
\end{pmatrix},
$$

ここで $\bar{\mathbb{O}}\in\mathbb{R}^{n\times{}n}$ および $\mathbb{O}\in\mathbb{R}^{(N - n)\times(N-n)}.$ ```
