Compute the offset between two time systems at a given Epoch.

The offset (in seconds) is computed as:

```
time_system_offset = tsys_dest - tsys_src
```

The value returned is the number of seconds that musted be added to the source time system given the input epoch, to get the equivalent epoch.

Conversions are accomplished using SOFA C library calls. Epoch.

Arguments:

  * `jd::Real`: Part 1 of two-part date (Julian days)
  * `fd::Real`: Part 2 of two-part date (Fractional days)
  * `tsys_src::String`: Base time system
  * `tsys_dest::String`: Destination time system

Returns:

  * `offset::Float`: Offset between soruce and destination time systems in seconds.
