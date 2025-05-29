```
StdString(str::String)
```

Create a `StdString` from the contents of the string. Any null-characters ('\0') will be included in the string such that `ncodeunits(str) == ncodeunits(StdString(str))`.
