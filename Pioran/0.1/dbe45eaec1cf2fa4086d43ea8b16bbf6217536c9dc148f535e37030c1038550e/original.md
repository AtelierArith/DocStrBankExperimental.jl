```
TwoLogUniformDependent(a, b, ϵ) 
TwoLogUniformDependent(a, b) (constructor with default ϵ = 1e-10
```

Multivariate distribution to model three random variables  where the first one x1 is given by log-U[a,b] and the second one x2 is given by log-U[x1,b].

  * `a`: lower bound of the first distribution
  * `b`: upper bound of the first distribution
  * `ϵ`: small value to make sure that the lower and upper bounds of each distribution are different

This means that the lower bound of the second distribution is dependent on the value of the first distribution. This is implemented to overcome the limitations of the current Turing's implementation for dependent priors with dynamic support. See the following issues for more details: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).
