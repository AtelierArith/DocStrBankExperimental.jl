```
sc_package_print_summary(log_priority)
```

Print a summary of all packages registered with SC. Uses the `SC_LC_GLOBAL` log category which by default only prints on rank 0.

### Parameters

  * `log_priority`:[in] Priority passed to sc log functions.

### Prototype

```c
void sc_package_print_summary (int log_priority);
```
