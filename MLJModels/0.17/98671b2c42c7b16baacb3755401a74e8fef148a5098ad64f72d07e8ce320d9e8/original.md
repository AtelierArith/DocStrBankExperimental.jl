```
load_path(model_name::String, pkg=nothing)
```

Return the load path for model type with name `model_name`, specifying the algorithm=providing package name `pkg` to resolve name conflicts, if necessary.

```
load_path(proxy::NamedTuple)
```

Return the load path for the model whose name is `proxy.name` and whose algorithm-providing package has name `proxy.package_name`. For example, `proxy` could be any element of the vector returned by `models()`.

```
load_path(model)
```

Return the load path of a `model` instance or type. Usually requires necessary model code to have been separately loaded. Supply strings as above if code is not loaded.
