```
textdump(io::IO, txt::AbstractString, base::Integer; offset = 0, len = -1)
```

Dump (with `baseddump`) the string `txt`. Julia strings will be interpreted as utf-8 text, with mulitbyte chars displayed in little endian order.

```
textdump(txt, base; offset = 0, len = -1)
```

This method is the same as the former one but dumps only to stdout.
