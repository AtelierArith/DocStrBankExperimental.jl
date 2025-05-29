```
AddonDebug(f :: Function)
```

This addon calls the function `f` over the output of the message mapping and products. The result is expected to be boolean and when returning true, it will throw an error with the debug information. Common applications of this addon are to check for NaNs and Infs in the messages and marginals. 

## Example

```julia
checkfornans(x) = isnan(x)
checkfornans(x::AbstractArray) = any(checkfornans.(x))
checkfornans(x::Tuple) = any(checkfornans.(x))

addons = (AddonDebug(dist -> checkfornans(params(dist))),)
```
