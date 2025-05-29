```
sc_finalize_noabort()
```

Unregisters all packages, runs the memory check, removes the signal handlers and resets sc_identifier and sc_root_*. This function never aborts but returns the number of errors encountered. This function is optional. This function does not require [`sc_init`](@ref) to be called first.

### Returns

0 when everything is consistent, nonzero otherwise.

### Prototype

```c
int sc_finalize_noabort (void);
```
