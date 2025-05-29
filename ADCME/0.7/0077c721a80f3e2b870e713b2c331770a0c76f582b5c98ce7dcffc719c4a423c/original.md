```
independent(o::PyObject, args...; kwargs...)
```

Returns `o` but when computing the gradients, the top gradients will not be back-propagated into dependent variables of `o`.
