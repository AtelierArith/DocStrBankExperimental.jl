```
registername(service, name::String, actor::Union{Addr,Actor})
```

Register the given actor under the given name in the scheduler-local name registry.

Note that there is no need to unregister the name when migrating or dying

# TODO implement manual and auto-unregistration
