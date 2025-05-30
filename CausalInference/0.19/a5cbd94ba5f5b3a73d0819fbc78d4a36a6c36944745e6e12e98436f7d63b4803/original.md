```
pcalg(g, I; stable=true)
```

Perform the PC algorithm for a set of 1:n variables using the tests

```
I(u, v, [s1, ..., sn])
```

Use `IClosure(I, args)` to wrap a function f with signature

```
f(u, v, [s1, ..., sn], par...)
```

Returns the CPDAG as DiGraph. By default uses a stable and threaded versions of the skeleton algorithm. (This is the most recent interface)
