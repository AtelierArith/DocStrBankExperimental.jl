```
olver(a, b, c, f, N; atol)
```

returns a vector `u` satisfying the 3-term recurrence relationship

```
-b[1]u[1] + c[1]u[2] = f[1]
a[k-1]u[k-1] + b[k]u[k] + c[k]u[k+1] = f[k]
```

It will compute at least `N` entries, but possibly more, returning the result when the backward error of the first `N` entries between consective truncations is less than `atol`.
