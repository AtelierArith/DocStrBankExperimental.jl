```
initialize(P::AbstractProcess)
```

This function is called before any control or measurement operations are performed. During a call to `initialize`, one might set up external communications etc. After control is done, the function [`finalize`](@ref) is called.
