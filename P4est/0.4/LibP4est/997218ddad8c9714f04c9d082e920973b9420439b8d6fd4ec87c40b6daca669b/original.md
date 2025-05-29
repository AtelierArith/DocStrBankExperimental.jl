```
p8est_find_higher_bound(array, q, guess)
```

Find the highest position tq in a quadrant array such that tq <= q.

### Returns

Returns the id of the matching quadrant or -1 if array > q or the array is empty.

### Prototype

```c
ssize_t p8est_find_higher_bound (sc_array_t * array, const p8est_quadrant_t * q, size_t guess);
```
