# Usage

```
solve(FDDE::FDDEProblem, dt, DelayPECE())
```

Using the delayed predictor-corrector method to solve the delayed fractional differential equation problem in the Caputo sense.

Capable of solving both single term FDDE and multiple FDDE, support time varying lags of course😋.

## References

@article{Wang2013ANM, title={A Numerical Method for Delayed Fractional-Order Differential Equations}, author={Zhen Wang}, journal={J. Appl. Math.}, year={2013}, volume={2013}, pages={256071:1-256071:7} }

@inproceedings{Nagy2014NUMERICALSF, title={NUMERICAL SIMULATIONS FOR VARIABLE-ORDER FRACTIONAL NONLINEAR DELAY DIFFERENTIAL EQUATIONS}, author={Abdelhameed M. Nagy and Taghreed Abdul Rahman Assiri}, year={2014} }

@inproceedings{Abdelmalek2019APM, title={A Predictor-Corrector Method for Fractional Delay-Differential System with Multiple Lags}, author={Salem Abdelmalek and Redouane Douaifia}, year={2019} }
