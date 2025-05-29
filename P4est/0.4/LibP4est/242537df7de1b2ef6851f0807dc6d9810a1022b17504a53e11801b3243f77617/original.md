```
p8est_search(p4est_, quadrant_fn, point_fn, points)
```

This function is provided for backwards compatibility. We call p8est*search*local with call_post = 0.

### Prototype

```c
void p8est_search (p8est_t * p4est, p8est_search_query_t quadrant_fn, p8est_search_query_t point_fn, sc_array_t * points);
```
