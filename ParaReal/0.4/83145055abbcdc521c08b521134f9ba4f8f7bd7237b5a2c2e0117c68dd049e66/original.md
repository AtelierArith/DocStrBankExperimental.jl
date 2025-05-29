```
solve!(::ParaReal.Pipeline)
```

Create and schedule the tasks executing the pipeline stages. Send the problem's initial value and wait for the completion of all stages. Throws an error if the pipeline failed.

Returns a [`Solution`](@ref).
