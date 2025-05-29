Newton CG solver. This is the same as the Newton solver except that instead of solving systems of the form `H\b` where `H` is the full Hessian, it uses a matrix-free conjugate gradient approach to solving that system. This should generally be preferred for larger scale cases.

`optim_options` are the [general Optim Options](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/). `newtoncg_options` are the [options of Krylov Trust Region method](https://github.com/JuliaNLSolvers/Optim.jl/blob/master/src/multivariate/solvers/second_order/krylov_trust_region.jl)

## Example

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.NewtonCG(
    optim_options = Optim.Options(time_limit = 20),
    newtoncg_options = (eta = 0.2,)
)
```
