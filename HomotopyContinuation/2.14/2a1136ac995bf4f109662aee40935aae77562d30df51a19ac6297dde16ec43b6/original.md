```
nsingular(
    result;
    counting_multiplicities = false,
    kwargs...,
)
```

The number of singular solutions. A solution is considered singular if its winding number is larger than 1 or the condition number is larger than `tol`. If `counting_multiplicities=true` the number of singular solutions times their multiplicities is returned.
