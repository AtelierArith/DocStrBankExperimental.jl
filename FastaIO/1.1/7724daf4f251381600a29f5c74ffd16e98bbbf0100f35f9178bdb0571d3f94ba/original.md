```
rewind(fr::FastaReader)
```

This function rewinds the reader, so that it can restart the parsing again without closing and re-opening it. It also resets the value of the `num_parsed` field.
