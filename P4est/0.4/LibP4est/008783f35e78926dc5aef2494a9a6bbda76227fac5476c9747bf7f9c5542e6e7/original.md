```
p6est_connectivity_new(conn4, top_vertices, height)
```

Create a [`p6est_connectivity_t`](@ref) from a [`p4est_connectivity_t`](@ref). All fields are copied, so all inputs can be safey destroyed.

### Parameters

  * `conn4`:[in] the 2D connectivity
  * `top_vertices`:[in] if NULL, then the sheet has a uniform vertical profile; otherwise, *top_vertices* gives teh vertices of the top of the sheet; should be the same size as *conn4*->tree*to*vertex
  * `height`:[in] if *top_vertices* == NULL, then this gives the offset fro the bottom of the sheet to the top.

### Returns

the 2D+1D connectivity information.

### Prototype

```c
p6est_connectivity_t *p6est_connectivity_new (p4est_connectivity_t * conn4, double *top_vertices, double height[3]);
```
