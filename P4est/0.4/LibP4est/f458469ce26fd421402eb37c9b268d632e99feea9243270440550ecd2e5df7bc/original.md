```
p8est_checksum(p8est_)
```

Compute the checksum for a forest. Based on quadrant arrays only. It is independent of partition and mpisize.

### Returns

Returns the checksum on processor 0 only. 0 on other processors.

### Prototype

```c
unsigned p8est_checksum (p8est_t * p8est);
```
