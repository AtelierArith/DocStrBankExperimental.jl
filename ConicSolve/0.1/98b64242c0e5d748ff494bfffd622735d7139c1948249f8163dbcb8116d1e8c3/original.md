```
mat(u)
```

Performs the inverse operation of vec(U), i.e. mat(vec(U)) = U

### Output

Returns a matrix representation of the vector u.

$$
\begin{bmatrix}
    u_{1}            & u_{2}/\sqrt{2}     & u_{3}/\sqrt{2}   & \dots  & u_{n}/\sqrt{2}     \\
    u_{2}/\sqrt{2}  & u_{p+1}             & u_{23}/\sqrt{2}  & \dots  & u_{2p-1}/\sqrt{2}  \\
    \vdots          & \vdots             & \vdots           &         & \vdots             \\
    u_{p}/\sqrt{2}  & u_{2p-1}/\sqrt{2}  & u_{d3}/\sqrt{2}  & \dots  & u_{p(p+1)/2}
\end{bmatrix}
$$
