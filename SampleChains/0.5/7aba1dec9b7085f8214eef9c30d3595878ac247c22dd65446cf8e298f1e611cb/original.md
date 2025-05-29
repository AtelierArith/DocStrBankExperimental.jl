```
function pushsample!(::AbstractChain, sample...) -> AbstractChain
```

Push a new sample to the chain. This is not `push!` because the sample may be represented across multiple arguments.
