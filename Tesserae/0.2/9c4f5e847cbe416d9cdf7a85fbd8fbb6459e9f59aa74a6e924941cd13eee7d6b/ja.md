```
SteffenBSpline(degree)
```

境界補正を伴うBスプラインカーネルである`SteffenBSpline`は、境界付近での統一の分割を満たします、$\sum_i w_{ip} = 1$。また、[`KernelCorrection`](@ref)も参照してください。

[^Steffen]: [Steffen, M., Kirby, R. M., & Berzins, M. (2008). Analysis and reduction of quadrature errors in the material point method (MPM). *International journal for numerical methods in engineering*, 76(6), 922-948.](https://doi.org/10.1002/nme.2360)
