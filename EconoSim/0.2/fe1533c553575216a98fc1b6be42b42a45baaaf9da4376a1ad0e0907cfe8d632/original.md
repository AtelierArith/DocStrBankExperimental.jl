```
produce!
```

Produces batch based on the producer and the provided resouces. The maximum possible batch is generated. The uses resources are removed from the resources Dict and produced Entities are added to the products Dict.

# Returns

A named tuple {products::Entities, resources::Entities, batches::Int64} where

  * products = produced entities
  * resources = leftover resources
  * batches = number of produced batches
