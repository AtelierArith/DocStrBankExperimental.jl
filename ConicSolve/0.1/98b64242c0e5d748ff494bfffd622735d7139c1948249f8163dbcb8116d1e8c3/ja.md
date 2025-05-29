```
mat(u)
```

ベクトル U の逆操作を実行します。すなわち、mat(vec(U)) = U

### 出力

ベクトル u の行列表現を返します。

$$
\begin{bmatrix}
    u_{1}            & u_{2}/\sqrt{2}     & u_{3}/\sqrt{2}   & \dots  & u_{n}/\sqrt{2}     \\
    u_{2}/\sqrt{2}  & u_{p+1}             & u_{23}/\sqrt{2}  & \dots  & u_{2p-1}/\sqrt{2}  \\
    \vdots          & \vdots             & \vdots           &         & \vdots             \\
    u_{p}/\sqrt{2}  & u_{2p-1}/\sqrt{2}  & u_{d3}/\sqrt{2}  & \dots  & u_{p(p+1)/2}
\end{bmatrix}
$$
