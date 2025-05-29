```
p4est_checksum_partition(p4est_)
```

Compute a partition-dependent checksum for a forest.

### Returns

Returns the checksum on processor 0 only. 0 on other processors.

### Prototype

```c
unsigned p4est_checksum_partition (p4est_t * p4est);
```
