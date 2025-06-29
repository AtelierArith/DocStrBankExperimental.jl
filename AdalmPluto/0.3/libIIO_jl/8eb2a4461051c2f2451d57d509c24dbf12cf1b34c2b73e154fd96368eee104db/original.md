```
C_iio_create_xml_context_mem(xml, length)
```

Create a context from XML data in memory.

# Parameters

  * `xml::String` : Pointer to the XML data in memory
  * `length::UInt` : Length of the XML string in memory (excluding the final  )

# Returns

  * On success, A pointer to an iio_context structure
  * On failure, if the assertions are enabled, an error is thrown.
  * On failure, if the assertions are disabled, NULL is returned.

# NOTE

The format of the XML must comply to the one returned by `iio_context_get_xml`

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gabaa848ca554af5723a44b9b7fd0ba6a3)
