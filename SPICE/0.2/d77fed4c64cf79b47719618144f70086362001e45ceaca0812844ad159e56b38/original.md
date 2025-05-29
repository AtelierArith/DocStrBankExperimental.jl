```
timdef(action, item, value="")
```

Set and retrieve the defaults associated with calendar input strings.

### Arguments

  * `action`: The kind of action to take, either `:SET` or `:GET`
  * `item`: The default item of interest. The items that may be requested are:

      * `:CALENDAR` with allowed values:

          * `"GREGORIAN"`
          * `"JULIAN"`
          * `"MIXED"`
      * `:SYSTEM` with allowed values:

          * `"TDB"`
          * `"TDT"`
          * `"UTC"`
      * `:ZONE` with allowed values (`0 <= HR < 13` and `0 <= MN < 60`):

          * `"EST"`
          * `"EDT"`
          * `"CST"`
          * `"CDT"`
          * `"MST"`
          * `"MDT"`
          * `"PST"`
          * `"PDT"`
          * `"UTC+$HR"`
          * `"UTC-$HR"`
          * `"UTC+$HR:$MN"`
          * `"UTC-$HR:$MN"`

### Output

Returns the value associated with the default item.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/timdef_c.html)
