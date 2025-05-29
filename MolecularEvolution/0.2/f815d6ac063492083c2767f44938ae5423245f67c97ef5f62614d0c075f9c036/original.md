```
allocate!(tree, partition_or_message)
```

Allocates initial messages for all nodes in the tree, copying the passed-in message template. If passed a partition, then this will assume the message template is a vector containing just that partition.
