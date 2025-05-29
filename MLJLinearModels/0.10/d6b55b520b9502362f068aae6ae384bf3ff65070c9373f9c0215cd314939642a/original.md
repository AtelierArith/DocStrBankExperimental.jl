LBFGS quasi-Newton solver. See [the wikipedia entry](https://en.wikipedia.org/wiki/Limited-memory_BFGS).

`optim_options` are the [general Optim Options](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/). `lbfgs_options` are the [options of LBFGS method](https://julianlsolvers.github.io/Optim.jl/stable/#algo/lbfgs/)

## Example

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.LBFGS(
    optim_options = Optim.Options(time_limit = 20),
    lbfgs_options = (linesearch = Optim.LineSearches.HagerZhang()),)
)
```
