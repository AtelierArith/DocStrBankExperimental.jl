```
ContractingRENParams(nv, A, B, C, D; ...)
```

Alternative constructor for `ContractingRENParams` that initialises the REN from a **stable** discrete-time linear system with state-space model

$$
\begin{align*}
x_{t+1} &= Ax_t + Bu_t \\
y_t &= Cx_t + Du_t.
\end{align*}
$$

[TODO:] This method has not been used or tested in a while. If you find it useful, please reach out to us and we will add full support and testing! :) [TODO:] Make compatible with αbar ≠ 1.0.
