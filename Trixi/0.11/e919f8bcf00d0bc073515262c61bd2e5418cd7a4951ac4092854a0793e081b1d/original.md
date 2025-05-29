```
vorticity(u, gradients, equations::CompressibleNavierStokesDiffusion3D)
```

Computes the (node-wise) vorticity, defined in 3D as

$$
    \omega = \nabla \times \boldsymbol{v} =
    \begin{pmatrix}
        \frac{\partial v_3}{\partial y} - \frac{\partial v_2}{\partial z} \\
        \frac{\partial v_1}{\partial z} - \frac{\partial v_3}{\partial x} \\
        \frac{\partial v_2}{\partial x} - \frac{\partial v_1}{\partial y}
    \end{pmatrix}
$$
