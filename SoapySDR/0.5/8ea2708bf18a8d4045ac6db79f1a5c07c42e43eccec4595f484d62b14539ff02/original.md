```
Devices()
Device(args...)
```

Enumerates all detectable SDR devices on the system. Indexing into the returned `Devices` object returns a list of keywords used to create a `Device` struct.

Optionally pass in a list of keywords to filter the returned list. Example:

```
Devices(driver="rtlsdr")
```
