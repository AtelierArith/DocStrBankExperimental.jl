```
sc_atol(nptr)
```

Safe version of the standard library atol (3) function.

### Parameters

  * `nptr`:[in] NUL-terminated string.

### Returns

Converted long value. 0 if no valid number. LONG_MAX on overflow, LONG_MIN on underflow.

### Prototype

```c
long sc_atol (const char *nptr);
```
