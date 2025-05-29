```
t8_shmem_array_allgather(sendbuf, sendcount, sendtype, recvarray, recvcount, recvtype)
```

### プロトタイプ

```c
void t8_shmem_array_allgather (const void *sendbuf, int sendcount, sc_MPI_Datatype sendtype, t8_shmem_array_t recvarray, int recvcount, sc_MPI_Datatype recvtype);
```
