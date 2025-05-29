```
sc_package_is_registered(package_id)
```

Query whether an identifier matches a registered package.

### Parameters

  * `package_id`:[in] Only a non-negative id can be registered.

### Returns

True if and only if the package id is non-negative and package is registered.

### Prototype

```c
int sc_package_is_registered (int package_id);
```
