```
p8est_checksum_partition(p8est_)
```

Compute a partition-dependent checksum for a forest.

### Returns

Returns the checksum on processor 0 only. 0 on other processors.

### Prototype

```c
unsigned p8est_checksum_partition (p8est_t * p8est);
```
