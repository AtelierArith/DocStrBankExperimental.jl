```
p8est_connectivity_reduce(conn)
```

Removes corner and edge information of a connectivity such that enough information is left to run [`p8est_connectivity_complete`](@ref) successfully. The reduced connectivity still passes [`p8est_connectivity_is_valid`](@ref).

### Parameters

  * `conn`:[in,out] The connectivity to be reduced.

### Prototype

```c
void p8est_connectivity_reduce (p8est_connectivity_t * conn);
```
