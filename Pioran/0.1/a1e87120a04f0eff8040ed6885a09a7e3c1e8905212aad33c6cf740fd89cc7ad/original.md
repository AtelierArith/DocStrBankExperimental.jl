```
TwoUniformDependent(a, b, c, ϵ)
TwoUniformDependent(a, b, c) (constructor with default ϵ = 1e-10)
```

Multivariate distribution to model two random variables  where the first one is given by U[a,b] and the second one is given by U[x,c],  where x is a random variable sampled from the first distribution. 

  * `a`: lower bound of the first distribution
  * `b`: upper bound of the first distribution
  * `c`: upper bound of the second distribution
  * `ϵ`: small value to make sure that the lower and upper bounds of each distribution are different

This means that the lower bound of the second distribution is dependent on the value of the first distribution.This is implemented to overcome the limitations of the current Turing's implementation for dependent priors with dynamic support. See the following issues for more details: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).

# Example

```jldoctest
julia> using Pioran, Distributions
julia> d = TwoUniformDependent(0, 1, 2)
TwoUniformDependent(0.0, 1.0, 2.0)

julia> rand(d)
2-element Array{Float64,1}:
 0.123
 1.234
```
