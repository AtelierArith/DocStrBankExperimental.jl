```
pgaspi_allreduce(buffer_send, buffer_receive, num, operation, datatyp, group, timeout_ms)
```

### Prototype

```c
gaspi_return_t pgaspi_allreduce (const gaspi_pointer_t buffer_send, gaspi_pointer_t const buffer_receive, const gaspi_number_t num, const gaspi_operation_t operation, const gaspi_datatype_t datatyp, const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
