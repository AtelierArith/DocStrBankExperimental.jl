```
C_iio_create_default_context()
```

Create a context from local or remote IIO devices.

# Returns

  * On success, A pointer to an iio_context structure
  * On failure, if the assertions are enabled, an error is thrown
  * On failure, if the assertions are disabled, NULL is returned

# NOTE

This function will create a network context if the IIOD_REMOTE environment variable is set to the hostname where the IIOD server runs. If set to an empty string, the server will be discovered using ZeroConf. If the environment variable is not set, a local context will be created instead.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga21076125f817a680e0c01d4a490f0416)
