```
execute!(rp::RedPitaya, batch::ScpiBatch)
```

Executes all commands of the given batch. Returns an array of the results in the order of the commands. An element is `nothing` if the command has no return value.
