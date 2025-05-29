```
reactant_device(;
    force::Bool=false, client=missing, device=missing, sharding=missing
) -> Union{ReactantDevice, CPUDevice}
```

Return a `ReactantDevice` object if functional. Otherwise, throw an error if `force` is `true`. Falls back to `CPUDevice` if `force` is `false`.

`client` and `device` are used to specify the client and particular device to use. If not specified, then the default client and index are used.

`sharding` is used to specify the sharding strategy. If a `Reactant.Sharding.AbstractSharding` is specified, then we use it to shard all abstract arrays. Alternatively, pass in a `IdDict` to specify the sharding for specific leaves.
