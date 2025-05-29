```
eFAST(; num_harmonics::Int = 4)
```

  * `num_harmonics`: the number of harmonics to sum in the Fourier series decomposition, this defaults to 4.

## Method Details

eFAST offers a robust, especially at low sample size, and computationally efficient procedure to get the first and total order indices as discussed in Sobol. It utilizes monodimensional Fourier decomposition along a curve, exploring the parameter space. The curve is defined by a set of parametric equations,

$$
x_{i}(s) = G_{i}(sin ω_{i}s), ∀ i=1,2 ,..., N
$$

where s is a scalar variable varying over the range $-∞ < s < +∞$, $G_{i}$ are transformation functions and ${ω_{i}}, ∀ i=1,2,...,N$ is a set of different (angular) frequencies, to be properly selected, associated with each factor for all $N$ (`samples`) number of parameter sets. For more details, on the transformation used and other implementation details you can go through [ A. Saltelli et al.](https://dx.doi.org/10.1080/00401706.1999.10485594).

## API

```
gsa(f, method::eFAST, p_range::AbstractVector; samples::Int, batch = false,
         distributed::Val{SHARED_ARRAY} = Val(false),
         rng::AbstractRNG = Random.default_rng(), kwargs...) where {SHARED_ARRAY}
```

Note, `p_range` is either a vector of tuples for the upper and lower bound or a vector of `Distribution`s. 

### Example

Below we show use of `eFAST` on the Ishigami function.

```julia
using GlobalSensitivity, QuasiMonteCarlo, Distributions

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

## define upper and lower limits, a.k.a uniform distributions
lb = -ones(4)*π
ub = ones(4)*π

res1 = gsa(ishi, eFAST(), [[lb[i],ub[i]] for i in 1:4], samples=15000)

# define distributions for the inputs
input_ranges = [Normal(0, 1),
                Uniform(-π, π),
                Uniform(-π, π),
                Uniform(-π, π)]

res2 = gsa(ishi, eFAST(), input_ranges, samples=15000)

## with batching
function ishi_batch(X)
    A= 7
    B= 0.1
    @. sin(X[1,:]) + A*sin(X[2,:])^2+ B*X[3,:]^4 *sin(X[1,:])
end

res3 = gsa(ishi_batch, eFAST(), [[lb[i],ub[i]] for i in 1:4], samples=15000, batch=true)
```
