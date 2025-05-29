```
p4est_ghost_exchange_custom_begin(p4est_, ghost, data_size, mirror_data, ghost_data)
```

Begin an asynchronous ghost data exchange by posting messages. The arguments are identical to [`p4est_ghost_exchange_custom`](@ref). The return type is always non-NULL and must be passed to [`p4est_ghost_exchange_custom_end`](@ref) to complete the exchange. The ghost data must not be accessed before completion. The mirror data can be safely discarded right after this function returns since it is copied into internal send buffers.

### Parameters

  * `mirror_data`:[in] Not required to stay alive any longer.
  * `ghost_data`:[in,out] Must stay alive into the completion call.

### Returns

Transient storage for messages in progress.

### Prototype

```c
p4est_ghost_exchange_t *p4est_ghost_exchange_custom_begin (p4est_t * p4est, p4est_ghost_t * ghost, size_t data_size, void **mirror_data, void *ghost_data);
```
