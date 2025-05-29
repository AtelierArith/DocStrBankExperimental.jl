```
DimMover(from, to)
```

Constructs a Dimension Mover Layer.

We can have Lux's conventional order `(data, channel, batch)` by using it as the last layer of `AbstractLuxLayer` to swap the batch-index and the time-index of the Neural DE's output considering that each time point is a channel.
