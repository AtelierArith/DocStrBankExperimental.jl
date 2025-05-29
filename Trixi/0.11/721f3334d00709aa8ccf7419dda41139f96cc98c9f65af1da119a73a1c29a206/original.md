```
vorticity(u, gradients, equations::CompressibleNavierStokesDiffusion2D)
```

Computes the (node-wise) vorticity, defined in 2D as

$$
    \omega = \nabla \times \boldsymbol{v} = \frac{\partial v_2}{\partial x_1} - \frac{\partial v_1}{\partial x_2}
$$
