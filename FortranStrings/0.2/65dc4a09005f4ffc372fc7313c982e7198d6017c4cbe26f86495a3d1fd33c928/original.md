```
SCAN(STRING, CHARSET, BACK=false)
```

Return the position of the start of the first occurrence of string `CHARSET` as a `CHARSET` in `STRING`, counting from one.

If `CHARSET` is not present in `STRING`, zero is returned. If the `BACK` argument is present and true, the return value is the start of the last occurrence rather than the first.
