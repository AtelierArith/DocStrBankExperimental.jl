```
HomogeneousBodyHeating
```

A model for single band light attenuation which heats the water in the form:

$$
I(x, y, z) = I_0(x, y) * \exp\left(-\alpha z\right),
$$

where $I$ is the radiation intensity and $\alpha$ is the attenuation coefficient. This heats the water like $\frac{\partial T(x, y, z)}{\partial t} = \frac{I(x, y, z)A}{c^p\rho}$ where $A$ is the area of the cell, $c^p$ is the specific heat capacity and $\rho$ is the water density. 
