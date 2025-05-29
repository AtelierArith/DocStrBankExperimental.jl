```
mutable struct ExplicitRENParams{T}
```

Explicit REN parameter struct.

These parameters define a recurrent equilibrium network with model inputs and outputs $u_t, y_t$, neuron inputs and outputs $v_t,w_t$, and states `x_t`.

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

See [Revay et al. (2021)](https://arxiv.org/abs/2104.05942) for more details on explicit parameterisations of REN.
