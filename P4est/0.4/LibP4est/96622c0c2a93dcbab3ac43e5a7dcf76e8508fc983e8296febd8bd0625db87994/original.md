```
sc_atoi(nptr)
```

Safe version of the standard library atoi (3) function.

### Parameters

  * `nptr`:[in] NUL-terminated string.

### Returns

Converted integer value. 0 if no valid number. INT_MAX on overflow, INT_MIN on underflow.

### Prototype

```c
int sc_atoi (const char *nptr);
```
