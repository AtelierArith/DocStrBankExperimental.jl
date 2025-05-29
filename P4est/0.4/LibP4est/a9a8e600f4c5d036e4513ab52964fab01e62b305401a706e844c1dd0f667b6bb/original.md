```
sc_package_set_abort_alloc_mismatch(package_id, set_abort)
```

Set the unregister behavior of [`sc_package_unregister`](@ref)().

### Parameters

  * `package_id`:[in] Must be -1 for the default package or the identifier of a registered package.
  * `set_abort`:[in] True if [`sc_package_unregister`](@ref)() should abort if the number of allocs does not match the number of frees; false otherwise.

### Prototype

```c
void sc_package_set_abort_alloc_mismatch (int package_id, int set_abort);
```
