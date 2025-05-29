```
C_iio_context_get_name(context)
```

Get the name of the given context.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure

# Returns

  * A NULL-terminated string

# NOTE

The returned string will be local, xml or network when the context has been created with the local, xml and network backends respectively.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gafed8e036873ad6f70c3db92c7136ad31)
