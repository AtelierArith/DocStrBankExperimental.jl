```
error_if_direct_mode(model::GenericModel, func::Symbol)
```

Errors if `model` is in direct mode during a call from the function named `func`.

Used internally within JuMP, or by JuMP extensions who do not want to support models in direct mode.

## Example

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> error_if_direct_mode(model, :foo)
ERROR: The `foo` function is not supported in DIRECT mode.
Stacktrace:
[...]
```
