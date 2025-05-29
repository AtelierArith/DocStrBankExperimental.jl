```
bn(args...;center = true, scale=true, kwargs...)
```

`bn` はキーワードパラメータ `is_training` を受け入れます。

# 例

```julia
bn(inputs, name="batch_norm", is_training=true)
```

!!! 注     `bn` は `control_dependency` と一緒に使用する必要があります。

````
```julia
update_ops = get_collection(UPDATE_OPS)
control_dependencies(update_ops) do 
    global train_step = AdamOptimizer().minimize(loss)
end 
```
````
