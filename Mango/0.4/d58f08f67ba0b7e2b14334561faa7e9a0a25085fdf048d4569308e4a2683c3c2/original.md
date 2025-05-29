```
shutdown(container)
```

Shutdown the container. Here all loops are closed, resources freed. It is recommended to use [`activate`](@ref)  instead of shutting down manually.
