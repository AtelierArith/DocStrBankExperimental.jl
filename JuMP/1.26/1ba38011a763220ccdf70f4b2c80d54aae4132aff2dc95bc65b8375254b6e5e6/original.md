```
value(p::NonlinearParameter)
```

Return the current value stored in the nonlinear parameter `p`.

## Example

```jldoctest
julia> model = Model();

julia> @NLparameter(model, p == 10)
p == 10.0

julia> value(p)
10.0
```
