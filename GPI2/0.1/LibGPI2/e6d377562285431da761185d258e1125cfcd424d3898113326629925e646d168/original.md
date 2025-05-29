```
gaspi_allreduce_user(buffer_send, buffer_receive, num, element_size, reduce_operation, reduce_state, group, timeout_ms)
```

### Prototype

```c
gaspi_return_t gaspi_allreduce_user (const gaspi_pointer_t buffer_send, gaspi_pointer_t const buffer_receive, const gaspi_number_t num, const gaspi_size_t element_size, gaspi_reduce_operation_t const reduce_operation, gaspi_reduce_state_t const reduce_state, const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
