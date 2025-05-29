```
C_iio_create_network_context(host)
```

Create a context from the network.

# Parameters

  * `host::String` : Hostname, IPv4 or IPv6 address where the IIO Daemon is running

# Returns

  * On success, A pointer to an iio_context structure
  * On failure, if the assertions are enabled, an error is thrown.
  * On failure, if the assertions are disabled, NULL is returned.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga8adf2ef4d2b62aa34201469cd7049617)
