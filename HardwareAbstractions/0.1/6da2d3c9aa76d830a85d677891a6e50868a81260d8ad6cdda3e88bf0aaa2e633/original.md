```
finalize(P::AbstractProcess)
```

This function is called after any control or measurement operations are performed. During a call to `finalize`, one might finalize external communications etc. Before control is done, the function [`initialize`](@ref) is called.
