```
C_iio_scan_block_destroy(scan_block)
```

Destroy the given scan block.

# Parameters

  * `block::Ptr{iio_scan_block}` : A pointer to an `iio_scan_block` structure

# NOTE

After that function, the `iio_scan_block` pointer shall be invalid.

Introduced in version 0.20.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga91f6902ca18c491f96627cadb88c5c0a)
