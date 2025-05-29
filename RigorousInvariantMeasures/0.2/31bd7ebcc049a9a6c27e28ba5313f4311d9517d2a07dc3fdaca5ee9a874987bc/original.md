```
convergencerateabstract(Bas::Ulam, D::Dynamic, norms)
```

Estimate the strong norm of $||L^n|_{U_0}||_s$ from `norms`, the bounds on the weak norm of the discretized operator

$||L_{h}^n|_{U_0}||_w$

This method was developed in  Stefano Galatolo, Isaia Nisoli, Benoît Saussol. An elementary way to rigorously estimate convergence to equilibrium and escape rates. Journal of Computational Dynamics, 2015, 2 (1) : 51-64. doi: 10.3934/jcd.2015.2.51
