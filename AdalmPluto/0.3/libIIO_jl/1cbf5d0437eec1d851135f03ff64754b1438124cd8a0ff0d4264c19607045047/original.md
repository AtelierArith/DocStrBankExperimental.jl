```
C_iio_scan_block_get_info(scan_block, index)
```

Get the `iio_context_info` for a particular context.

# Parameters

  * `scan_block::Ptr{iio_scan_block}` : A pointer to an `iio_scan_block` structure
  * `index::UInt32` : The index corresponding to the context.

# Returns

  * On success, a pointer to the specified `iio_context_info`
  * On failure, NULL is returned and errno is set appropriately

Introduced in version 0.20.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga98c087491e97eb7e25999e3f29263e98)
