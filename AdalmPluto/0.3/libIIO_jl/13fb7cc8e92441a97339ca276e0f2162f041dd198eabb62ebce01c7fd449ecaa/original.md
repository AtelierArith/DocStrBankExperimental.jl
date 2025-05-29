```
C_iio_scan_context_destroy(scan_context)
```

Destroy the given scan context.

# Parameters

  * `scan_context::Ptr{iio_scan_context}` : A pointer to an `iio_scan_context` structure

# NOTE

After that function, the `iio_scan_context pointer` shall be invalid.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga649d7821636c744753067e8301a84e6d)
