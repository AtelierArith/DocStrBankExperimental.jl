```
C_iio_scan_context_get_info_list(scan_context, context_info)
```

Enumerate available contexts.

# Parameters

  * `scan_context::Ptr{iio_scan_context}` : A pointer to an `iio_scan_context` structure
  * `context_info::Ref{Ptr{Ptr{iio_context_info}}}` : A pointer to a `const struct iio_context_info **` typed variable. The pointed variable will be initialized on success.

# Returns

  * On success, the number of contexts found.
  * On failure, a negative error number.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga5d364d8d008bdbfe5486e6329d06257f)
