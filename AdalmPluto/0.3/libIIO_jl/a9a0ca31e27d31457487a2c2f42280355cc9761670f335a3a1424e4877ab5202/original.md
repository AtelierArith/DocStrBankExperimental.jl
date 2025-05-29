```
C_iio_create_scan_block(backend, flags)
```

Create a scan block.

# Parameters

  * `backend::String`: A NULL-terminated string containing the backend to use for scanning. If NULL, all the available backends are used.
  * `flags::UInt32` : Unused for now. Set to 0.

# Returns

  * On success, a pointer to a `iio_scan_block` structure
  * On failure, NULL is returned and errno is set appropriately

Introduced in version 0.20.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gad7fd2ea05bf5a8cebaff26b60edb8a13)
