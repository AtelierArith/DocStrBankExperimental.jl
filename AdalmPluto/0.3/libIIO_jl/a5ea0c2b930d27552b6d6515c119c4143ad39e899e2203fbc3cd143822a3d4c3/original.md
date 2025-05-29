```
C_iio_context_clone(context)
```

Duplicate a pre-existing IIO context.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure

# Returns

  * On success, A pointer to an iio_context structure
  * On failure, throws an error if the assertions are enabled, or NULL otherwise.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga1815e7c39b9a69aa11cf948b0433df01)
