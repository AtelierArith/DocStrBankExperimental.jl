```
C_iio_context_get_device(context, index)
```

Get the device present at the given index.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure
  * `index::UInt32` : The index corresponding to the device

# Returns

  * On success, a pointer to an iio_device structure
  * If the index is invalid and the assertions are enabled, an error is thrown.
  * If the index is invalid and the assertions are disabled, NULL is returned.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga3f2813ff34bf96c7c85dd05909f1c709)
