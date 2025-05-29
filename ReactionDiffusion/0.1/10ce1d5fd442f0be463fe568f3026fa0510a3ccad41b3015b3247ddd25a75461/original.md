```
get_param(model, turing_params, name, type)
```

For a given `model` and a (potentially large) number of pattern-forming parameter sets, `turing_params`, this function extracts the parameter values prescribed by the input `name`. For reaction parameters, used `type="reaction"`, for diffusion constants, use `type="diffusion"`.

Example:

```julia
δ₁ = get_param(model, turing_params,"δ₁","reaction")
D_COMPLEX = get_param(model, turing_params,"COMPLEX","diffusion")
```
