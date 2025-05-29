```
t8_element_MPI_Pack(ts, elements, count, send_buffer, buffer_size, position, comm)
```

### プロトタイプ

```c
void t8_element_MPI_Pack (const t8_eclass_scheme_c *ts, t8_element_t **const elements, const unsigned int count, void *send_buffer, const int buffer_size, int *position, sc_MPI_Comm comm);
```
