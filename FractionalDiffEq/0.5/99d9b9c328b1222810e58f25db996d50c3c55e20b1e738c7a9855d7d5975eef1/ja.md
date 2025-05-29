```
solve(prob::FODEProblem, Trapezoidal(); abstol=1e-3, maxiters=1e3)
```

生成関数 $f(x)=\frac{1+x}{2(1-x)^\alpha}$ を用いた [Trapezoidal](https://en.wikipedia.org/wiki/Trapezoidal_rule_(differential_equations)) を使用して、FODEのシステムを解くための重みを生成する分数線形多段法。

## 参考文献

@article{Garrappa2015TrapezoidalMF, title={Trapezoidal methods for fractional differential equations: Theoretical and computational aspects}, author={Roberto Garrappa}, journal={ArXiv}, year={2015}, volume={abs/1912.09878} }
