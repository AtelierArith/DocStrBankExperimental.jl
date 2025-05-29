```
sc_package_set_verbosity(package_id, log_priority)
```

Set the logging verbosity of a registered package. This can be called at any point in the program, any number of times. It can only lower the verbosity at and below the value of `SC_LP_THRESHOLD`.

### Parameters

  * `package_id`:[in] Must be a registered package identifier.

### Prototype

```c
void sc_package_set_verbosity (int package_id, int log_priority);
```
