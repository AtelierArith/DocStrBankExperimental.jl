```
p4est_init(log_handler, log_threshold)
```

Registers `p4est` with the SC Library and sets the logging behavior. This function is optional. This function must only be called before additional threads are created. If this function is not called or called with log_handler == NULL, the default SC log handler will be used. If this function is not called or called with log_threshold == `SC_LP_DEFAULT`, the default SC log threshold will be used. The default SC log settings can be changed with [`sc_set_log_defaults`](@ref) ().

### Prototype

```c
void p4est_init (sc_log_handler_t log_handler, int log_threshold);
```
