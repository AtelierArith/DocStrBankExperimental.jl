```julia
struct Twist{T}
```

ツイストは、2つの物体間の相対的な角運動と線運動を表します。

フレーム $j$ のツイストは、フレーム $i$ に対して、フレーム $k$ で表現され、次のように定義されます。

$$
T_{j}^{k,i}=\left(\begin{array}{c}
\omega_{j}^{k,i}\\
v_{j}^{k,i}
\end{array}\right)\in\mathbb{R}^{6}
$$

このとき、

$$
\left[\begin{array}{cc}
\hat{\omega}_{j}^{k,i} & v_{j}^{k,i}\\
0 & 0
\end{array}\right]=H_{i}^{k}\dot{H}_{j}^{i}H_{k}^{j}
$$

ここで、$H^{\beta}_{\alpha}$ はフレーム $\alpha$ からフレーム $\beta$ への同次変換であり、$\hat{x}$ はすべての $y \in \mathbb{R}^3$ に対して $\hat{x} y = x \times y$ を満たす $3 \times 3$ の斜対称行列です。

ここで、$\omega_{j}^{k,i}$ は角の部分であり、$v_{j}^{k,i}$ は線の部分です。線の部分は一般にフレーム $j$ の原点の線速度と同じではないことに注意してください。
