```
C_iio_context_get_attr(context, index)
```

Retrieve the name and value of a context-specific attribute.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure
  * `index::UInt32` : The index corresponding to the attribute

# Returns

  * On success, `(0, name::String, value::String)` is returned.
  * On error, `(errno, "", "")` is returned, where errno is a negative code.

Introduced in version 0.9.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga477dfddaefe0acda401f600247e13fc7)
