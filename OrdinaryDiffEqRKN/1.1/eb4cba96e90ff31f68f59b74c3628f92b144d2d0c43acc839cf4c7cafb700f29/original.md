```
DPRKN6FM
```

6th order explicit Runge-Kutta-Nyström method. The second order ODE should not depend on the first derivative.

Compared to [`DPRKN6`](@ref), this method has smaller truncation error coefficients which leads to performance gain when only the main solution points are considered.

## References

@article{Dormand1987FamiliesOR, title={Families of Runge-Kutta-Nystrom Formulae}, author={J. R. Dormand and Moawwad E. A. El-Mikkawy and P. J. Prince}, journal={Ima Journal of Numerical Analysis}, year={1987}, volume={7}, pages={235-250} }
