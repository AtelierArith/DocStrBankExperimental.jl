```
masterTrigger(rpc::RedPitayaCluster, val::Bool)
```

Set the master trigger of the cluster to `val`.

For `val` equals to true this is the same as calling the function on the RedPitaya returned by `master(rpc)`. If `val` is false then the keepAliveReset is set to true for all RedPitayas in the cluster before the master trigger is disabled. Afterwards the keepAliveReset is set to false again.

See also [`master`](@ref), [`keepAliveReset!`](@ref).
