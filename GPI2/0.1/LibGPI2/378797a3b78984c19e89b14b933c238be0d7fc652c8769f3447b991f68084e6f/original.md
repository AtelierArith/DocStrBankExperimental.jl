```
gaspi_allreduce(buffer_send, buffer_receive, num, operation, datatype, group, timeout_ms)
```

All Reduce collective operation.

### Parameters

  * `buffer_send`: The buffer with data for the operation.
  * `buffer_receive`: The buffer to receive the result of the operation.
  * `num`: The number of data elements in the buffer (beware of maximum - use [`gaspi_allreduce_elem_max`](@ref)).
  * `operation`: The type of operations (see [`gaspi_operation_t`](@ref)).
  * `datatyp`: Type of data (see [`gaspi_datatype_t`](@ref)).
  * `group`: The group involved in the operation.
  * `timeout_ms`: Timeout in milliseconds (or GASPI_BLOCK/GASPI_TEST).

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error, GASPI_TIMEOUT in case of timeout.

### Prototype

```c
gaspi_return_t gaspi_allreduce (const gaspi_pointer_t buffer_send, gaspi_pointer_t const buffer_receive, const gaspi_number_t num, const gaspi_operation_t operation, const gaspi_datatype_t datatype, const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
