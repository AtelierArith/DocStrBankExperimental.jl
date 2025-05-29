```
solve(prob::FODEProblem, Trapezoidal(); abstol=1e-3, maxiters=1e3)
```

Use [Trapezoidal](https://en.wikipedia.org/wiki/Trapezoidal_rule_(differential_equations)) with generating function $f(x)=\frac{1+x}{2(1-x)^\alpha}$ generated weights fractional linear multiple steps method to solve system of FODE.

## References

@article{Garrappa2015TrapezoidalMF, title={Trapezoidal methods for fractional differential equations: Theoretical and computational aspects}, author={Roberto Garrappa}, journal={ArXiv}, year={2015}, volume={abs/1912.09878} }
