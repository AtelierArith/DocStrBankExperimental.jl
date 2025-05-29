```
C_iio_scan_block_scan(scan_block)
```

Enumerate available contexts via scan block.

# Parameters

  * `scan_block::Ptr{iio_scan_block}` : A pointer to a `iio_scan_block` structure.

# Returns

  * On success, the number of contexts found.
  * On failure, a negative error number.

Introduced in version 0.20.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gaee7e04572c3b4d202cd0043bb8cee642)
