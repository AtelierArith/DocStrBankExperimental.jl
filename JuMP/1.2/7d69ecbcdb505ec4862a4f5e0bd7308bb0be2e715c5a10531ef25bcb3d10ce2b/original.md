```
set_value(p::NonlinearParameter, v::Number)
```

Store the value `v` in the nonlinear parameter `p`.

# Example

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, p == 0)
set_value(p, 5)
value(p)

# output
5.0
```
