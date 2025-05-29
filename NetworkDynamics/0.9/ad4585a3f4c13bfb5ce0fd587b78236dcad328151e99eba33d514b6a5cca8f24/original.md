```
abstract type Aggregator end
```

Abstract sypertype for aggregators. Aggregators operate on the output buffer of all components and fill the aggregation buffer with the aggregatated edge values per vertex.

All aggregators have the constructor

```
Aggegator(aggfun)
```

for example

```
SequentialAggreator(+)
```
