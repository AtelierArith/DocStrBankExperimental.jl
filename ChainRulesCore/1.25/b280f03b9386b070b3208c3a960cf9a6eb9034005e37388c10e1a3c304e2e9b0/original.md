```
ignore_derivatives(f::Function)
```

Tells the AD system to ignore the gradients of the wrapped closure. The primal computation (forward pass) is executed normally.

```julia
ignore_derivatives() do
    value = rand()
    push!(collection, value)
end
```

Using this incorrectly could lead to incorrect gradients. For example, the following function will have zero gradients with respect to its argument:

```julia
function wrong_grads(x)
    y = ones(3)
    ignore_derivatives() do
        push!(y, x)
    end
    return sum(y)
end
```
