```
t8_shmem_array_prefix(sendbuf, recvarray, count, type, op, comm)
```

### プロトタイプ

```c
void t8_shmem_array_prefix (const void *sendbuf, t8_shmem_array_t recvarray, const int count, sc_MPI_Datatype type, sc_MPI_Op op, sc_MPI_Comm comm);
```
