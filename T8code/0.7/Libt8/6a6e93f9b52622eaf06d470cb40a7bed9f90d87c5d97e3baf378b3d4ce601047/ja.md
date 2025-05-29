```
t8_shmem_array_allgatherv(sendbuf, sendcount, sendtype, recvarray, recvtype, comm)
```

### プロトタイプ

```c
void t8_shmem_array_allgatherv (void *sendbuf, const int sendcount, sc_MPI_Datatype sendtype, t8_shmem_array_t recvarray, sc_MPI_Datatype recvtype, sc_MPI_Comm comm);
```
