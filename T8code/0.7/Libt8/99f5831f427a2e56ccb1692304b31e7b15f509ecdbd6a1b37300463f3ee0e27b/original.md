```
t8_scheme_cxx_unref(pscheme)
```

Decrease the reference counter of a scheme. If the counter reaches zero, this scheme is destroyed.

# Arguments

  * `pscheme`:[in,out] On input, the scheme pointed to must exist with positive reference count. If the reference count reaches zero, the scheme is destroyed and this pointer set to NULL. Otherwise, the pointer is not changed and the scheme is not modified in other ways.

### Prototype

```c
void t8_scheme_cxx_unref (t8_scheme_cxx_t **pscheme);
```
