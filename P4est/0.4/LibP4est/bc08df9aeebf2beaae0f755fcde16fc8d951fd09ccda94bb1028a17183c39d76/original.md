```
sc_package_register(log_handler, log_threshold, name, full)
```

Register a software package with SC. This function must only be called before additional threads are created. The logging parameters are as in [`sc_set_log_defaults`](@ref).

### Returns

Returns a unique package id.

### Prototype

```c
int sc_package_register (sc_log_handler_t log_handler, int log_threshold, const char *name, const char *full);
```
