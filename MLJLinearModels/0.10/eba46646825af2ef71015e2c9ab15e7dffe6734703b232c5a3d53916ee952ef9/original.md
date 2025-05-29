Newton solver. This is a full Hessian solver and should be avoided for "large scale" cases.

`optim_options` are the [general Optim Options](https://julianlsolvers.github.io/Optim.jl/stable/#user/config/). `newton_options` are the [options of Newton's method](https://julianlsolvers.github.io/Optim.jl/stable/#algo/newton/)

## Example

```julia
using MLJLinearModels, Optim

solver = MLJLinearModels.Newton(
    optim_options = Optim.Options(time_limit = 20),
    newton_options = (linesearch = Optim.LineSearches.HagerZhang()),)
)
```
