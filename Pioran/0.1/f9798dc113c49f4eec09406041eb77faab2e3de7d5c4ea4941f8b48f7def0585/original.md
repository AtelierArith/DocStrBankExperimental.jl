```
ThreeUniformDependent(a, b, c, ϵ)
ThreeUniformDependent(a, b, c) (constructor with default ϵ = 1e-10)
```

Multivariate distribution to model three random variables  where the first one x1 is given by U[a,b] and the second one x2 is given by U[x1,c] and the third one x3 is given by U[x2,c]. where a<b<c.

  * `a`: lower bound of the first distribution
  * `b`: upper bound of the first distribution
  * `c`: upper bound of the second and third distribution
  * `ϵ`: small value to make sure that the lower and upper bounds of each distribution are different

This means that the lower bound of the second distribution is dependent on the value of the first distribution and so on... This is implemented to overcome the limitations of the current Turing's implementation for dependent priors with dynamic support. See the following issues for more details: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).
