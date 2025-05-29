```
C_iio_create_scan_context(backend, flags)
```

Create a scan context.

# Parameters

  * `backend::String` : A NULL-terminated string containing the backend(s) to use for scanning (example: pre version 0.20 : "local", "ip", or "usb"; post version 0.20 can handle multiple, including "local:usb:", "ip:usb:", "local:usb:ip:"). If NULL, all the available backends are used.
  * `flags::UInt32` : Unused for now. Set to 0.

# Returns

  * On success, a pointer to a `iio_scan_context` structure
  * On failure, NULL is returned and errno is set appropriately

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gaa333dd2e410a2769cf5685019185d99c)
