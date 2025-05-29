```
if_else(condition::Union{PyObject,Array,Bool}, fn1, fn2, args...;kwargs...)
```

  * If `condition` is a scalar boolean, it outputs `fn1` or `fn2` (a function with no input argument or a tensor) based on whether `condition` is true or false.
  * If `condition` is a boolean array, if returns `condition .* fn1 + (1 - condition) .* fn2`

!!! info
    If you encounter an error like this:

    ```
    tensorflow.python.framework.errors_impl.InvalidArgumentError: Retval[0] does not have value
    ```

    It's probably that your code within `if_else` is not valid.

