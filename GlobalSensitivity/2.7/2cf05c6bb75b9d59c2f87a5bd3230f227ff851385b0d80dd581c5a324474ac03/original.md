```
Shapley(n_perms, n_var, n_outer, n_inner)
```

  * `n_perms`: number of permutations to consider. Defaults to -1, which means all permutations           are considered hence the exact Shapley effects           algorithm is used. If `n_perms` is set to a positive integer, then the random version           of Shapley effects is used.
  * `n_var`: size of each bootstrapped sample
  * `n_outer`: number of samples to be taken to estimate conditional variance
  * `n_inner`: size of each `n_outer` sample taken

## Method Details

Shapely effects is a variance based method to assign attribution to each feature based on how sentitive the function to the feature. Shapley effects take into account that features could be dependent, which is not possible in previous methods like Sobol indices. In our implementation, we use Copulas.jl to define the joint input distribution as a SklarDist.

## API

```
gsa(f, method::Shapley, input_distribution::SklarDist; batch=false)
```

### Example

```julia
using Copulas, Distributions, GlobalSensitivity

function ishi(X)
    A = 7
    B = 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

function ishi_batch(X)
    A = 7
    B = 0.1
    @. sin(X[1, :]) + A*sin(X[2, :])^2+ B*X[3, :]^4 *sin(X[1, :])
end

n_perms = -1; # -1 indicates that we want to consider all permutations. One can also use n_perms > 0
n_var = 1000;
n_outer = 100;
n_inner = 3

dim = 3;
margins = (Uniform(-pi, pi), Uniform(-pi, pi), Uniform(-pi, pi));
dependency_matrix = Matrix(I, dim, dim)

C = GaussianCopula(dependency_matrix);
input_distribution = SklarDist(C,margins);

method = Shapley(n_perms=n_perms, n_var = n_var, n_outer = n_outer, n_inner = n_inner);

###### non-batch
result_non_batch = gsa(ishi,method,input_distribution,batch=false)
shapley_effects = result_non_batch.shapley_effects
println(shapley_effects)

###### batch
result_batch = gsa(ishi_batch,method,input_distribution,batch=true)
shapley_effects = result_batch.shapley_effects
println(shapley_effects)

#### Example with correlated inputs
d = 3
mu = zeros(d)
sig = [1, 1, 2]
ro = 0.9
Cormat = [1 0 0; 0 1 ro; 0 ro 1]
Covmat = (sig * transpose(sig)) .* Cormat

margins = [Normal(mu[i], sig[i]) for i in 1:d]
copula = GaussianCopula((sig * transpose(sig)) .* Cormat)
input_distribution = SklarDist(copula, margins)

result = gsa(ishi, method, input_distribution, batch = false)
```
