```
C_iio_create_xml_context(xml_file)
```

Create a context from a XML file.

# Parameters

  * `xml_file::String` : Path to the XML file to open

# Returns

  * On success, A pointer to an iio_context structure
  * On failure, if the assertions are enabled, an error is thrown.
  * On failure, if the assertions are disabled, NULL is returned.

# NOTE

The format of the XML must comply to the one returned by `iio_context_get_xml`.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga9925a84e596c3003e30b1cdd2b65d029)
