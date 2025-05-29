```
C_iio_context_find_device(context, name)
```

Try to find a device structure by its name of ID.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure
  * `name::String` : A NULL-terminated string corresponding to the name or the ID of the device to search for

# Returns

  * On success, a pointer to an iio_device structure
  * If the name or ID does not correspond to any known device, an error is thrown if the assertions are enabled, or NULL otherwise.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gade1dadfb5bc3c3b236add67f803c50c3)
