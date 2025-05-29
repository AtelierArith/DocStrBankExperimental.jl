```
p4est_checksum(p4est_)
```

Compute the checksum for a forest. Based on quadrant arrays only. It is independent of partition and mpisize.

### Returns

Returns the checksum on processor 0 only. 0 on other processors.

### Prototype

```c
unsigned p4est_checksum (p4est_t * p4est);
```
