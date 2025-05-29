```
value(p::NonlinearParameter)
```

Return the current value stored in the nonlinear parameter `p`.

# Example

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, p == 10)
value(p)

# output
10.0
```
