```
t8_scheme_cxx_ref(scheme)
```

Increase the reference counter of a scheme.

# Arguments

  * `scheme`:[in,out] On input, this scheme must be alive, that is, exist with positive reference count.

### Prototype

```c
void t8_scheme_cxx_ref (t8_scheme_cxx_t *scheme);
```
