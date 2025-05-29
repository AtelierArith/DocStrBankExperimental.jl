```
gaspi_state_vec_get(state_vector)
```

Get the state vector.

### Parameters

  * `state_vector`: Vector with state of each rank. The vector must be allocated with enough place to hold the state of all ranks.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_state_vec_get (gaspi_state_vector_t state_vector);
```
