```
bn(args...;center = true, scale=true, kwargs...)
```

`bn` accepts a keyword parameter `is_training`. 

# Example

```julia
bn(inputs, name="batch_norm", is_training=true)
```

!!! note
    `bn` should be used with `control_dependency`

    ```julia
    update_ops = get_collection(UPDATE_OPS)
    control_dependencies(update_ops) do 
        global train_step = AdamOptimizer().minimize(loss)
    end 
    ```

