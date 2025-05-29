```
execute!(rpc::RedPitayaCluster, batch::ScpiBatch)
```

Executes all commands of the given batch. Returns an array of the results in the order of the commands.

Each element of the result array is again an array containing the return values of the RedPitayas. An element of an inner array is `nothing` if the command has no return value.
