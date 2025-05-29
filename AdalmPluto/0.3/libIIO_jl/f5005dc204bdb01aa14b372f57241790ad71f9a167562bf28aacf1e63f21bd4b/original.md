```
C_iio_context_get_attr_value(context, name)
```

Retrieve the value of a context-specific attribute.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure
  * `name::String` : The name of the context attribute to read

Returns

  * On success, a NULL-terminated string.
  * If the name does not correspond to any attribute and the assertions are enabled, throws an error.
  * If the name does not correspond to any attribute and the assertions are disabled, returns an empty string.

Introduced in version 0.9.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga6394d108d425e4a6ed28d00c0e93d6ed)
