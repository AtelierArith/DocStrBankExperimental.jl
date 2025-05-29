```
DPRKN8
```

8th order explicit Runge-Kutta-Nyström method. The second order ODE should not depend on the first derivative.

Not as efficient as [`DPRKN12`](@ref) when high accuracy is needed, however this solver is competitive with [`DPRKN6`](@ref) at lax tolerances and, depending on the problem, might be a good option between performance and accuracy.

## References

@article{dormand1987high, title={High-order embedded Runge-Kutta-Nystrom formulae}, author={Dormand, JR and El-Mikkawy, MEA and Prince, PJ}, journal={IMA Journal of Numerical Analysis}, volume={7}, number={4}, pages={423–430}, year={1987}, publisher={Oxford University Press} }
