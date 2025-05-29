```
sc_abort_verbose(filename, lineno, msg)
```

Print a message to stderr and then call [`sc_abort`](@ref) ().

### Prototype

```c
void sc_abort_verbose (const char *filename, int lineno, const char *msg) __attribute__ ((noreturn));
```
