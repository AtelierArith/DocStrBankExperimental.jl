```
p4est_ghost_exchange_data_begin(p4est_, ghost, ghost_data)
```

Begin an asynchronous ghost data exchange by posting messages. The arguments are identical to [`p4est_ghost_exchange_data`](@ref). The return type is always non-NULL and must be passed to [`p4est_ghost_exchange_data_end`](@ref) to complete the exchange. The ghost data must not be accessed before completion.

### Parameters

  * `ghost_data`:[in,out] Must stay alive into the completion call.

### Returns

Transient storage for messages in progress.

### Prototype

```c
p4est_ghost_exchange_t *p4est_ghost_exchange_data_begin (p4est_t * p4est, p4est_ghost_t * ghost, void *ghost_data);
```
