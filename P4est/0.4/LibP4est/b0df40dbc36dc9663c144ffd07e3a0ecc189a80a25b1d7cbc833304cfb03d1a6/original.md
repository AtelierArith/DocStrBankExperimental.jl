```
sc_finalize()
```

Unregisters all packages, runs the memory check, removes the signal handlers and resets sc_identifier and sc_root_*. This function aborts on any inconsistency found unless the global variable default_abort_mismatch is false. This function is optional. This function does not require [`sc_init`](@ref) to be called first.

### Prototype

```c
void sc_finalize (void);
```
