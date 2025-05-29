```
sc_set_abort_handler(abort_handler)
```

Controls the default SC abort behavior.

### Parameters

  * `abort_handler`:[in] Set default SC above handler (NULL selects builtin). ***This function should not return!***

### Prototype

```c
void sc_set_abort_handler (sc_abort_handler_t abort_handler);
```
