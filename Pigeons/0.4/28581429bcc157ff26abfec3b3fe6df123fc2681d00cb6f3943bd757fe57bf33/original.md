```julia
watch(result; machine, last, interactive)

```

Print the queue status as well as the standard out  and error streams (merged) for the given `machine`. 

Note: when using control-c on interactive = true,          julia tends to crash as of version 1.8. 
