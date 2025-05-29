```
t8_element_vertex_reference_coords(ts, t, vertex, coords)
```

Compute the coordinates of a given element vertex inside a reference tree that is embedded into [0,1]^d (d = dimension).

!!! warning
    coords should be zero-initialized, as only the first d coords will be set, but when used elsewhere all coords might be used.


# Arguments

  * `t`:[in] The element to be considered.
  * `vertex`:[in] The id of the vertex whose coordinates shall be computed.
  * `coords`:[out] An array of at least as many doubles as the element's dimension whose entries will be filled with the coordinates of *vertex*.

### Prototype

```c
void t8_element_vertex_reference_coords (const t8_eclass_scheme_c *ts, const t8_element_t *t, const int vertex, double coords[]);
```
