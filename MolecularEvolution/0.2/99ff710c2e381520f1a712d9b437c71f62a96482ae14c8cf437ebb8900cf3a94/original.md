```
partition2obs(part::Partition)
```

Extracts the most likely state from a Partition, transforming it into a convenient type. For example, a NucleotidePartition will be transformed into a nucleotide sequence of type String. Note: You should overload this for your own Partititon types.
