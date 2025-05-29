```
release(o::InferenceSession)::Nothing
```

Release memory allocated to an [`InferenceSession`](@ref). This also happens automatically when the object has gone out of scope and the garbage collector deletes it.

However, there is no guarantee when that happens, so it can be useful to manually release the memory. This is especially true when the model has allocated GPU memory, which does not put pressure on the garbage collector to run promptly.

Using the inference session after releasing is an error.
