```
fits_read_keyword(f::FITSFile, keyname::String) -> (value, comment)
```

yields the specified keyword value and commend (as a tuple of strings), throws and error if the keyword is not found.
