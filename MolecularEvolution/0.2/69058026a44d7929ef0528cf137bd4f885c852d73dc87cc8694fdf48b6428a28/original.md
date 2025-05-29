```
combine!(dest::P, src::P) where P<:Partition
```

Combines evidence from two partitions of the same type, storing the result in dest. Note: You should overload this for your own Partititon types.
