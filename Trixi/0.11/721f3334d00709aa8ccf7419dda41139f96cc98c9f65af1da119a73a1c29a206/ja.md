```
vorticity(u, gradients, equations::CompressibleNavierStokesDiffusion2D)
```

2Dで定義された（ノードごとの）渦度を計算します。

$$
    \omega = \nabla \times \boldsymbol{v} = \frac{\partial v_2}{\partial x_1} - \frac{\partial v_1}{\partial x_2}
$$
