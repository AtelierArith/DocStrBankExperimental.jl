```
mutable struct ExplicitRENParams{T}
```

明示的RENパラメータ構造体。

これらのパラメータは、モデル入力と出力 $u_t, y_t$、ニューロンの入力と出力 $v_t,w_t$、および状態 `x_t` を持つ再帰的平衡ネットワークを定義します。

$$
\begin{equation*}
\begin{bmatrix}
x_{t+1} \\ v_t \\ y_t
\end{bmatrix}
= 
\begin{bmatrix}
A & B_1 & B_2 \\
C_1 & D_{11} & D_{12} \\
C_2 & D_{21} & D_{22} \\
\end{bmatrix}
\begin{bmatrix}
x_t \\ w_t \\ u_t
\end{bmatrix}
+ 
\begin{bmatrix}
b_x \\ b_v \\ b_y
\end{bmatrix}
\end{equation*}
$$

明示的なRENのパラメータ化に関する詳細は、[Revay et al. (2021)](https://arxiv.org/abs/2104.05942)を参照してください。
