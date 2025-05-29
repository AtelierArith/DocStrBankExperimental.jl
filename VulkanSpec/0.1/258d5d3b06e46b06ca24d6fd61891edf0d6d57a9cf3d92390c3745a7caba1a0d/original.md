```
len(pCode)
```

Return the function parameter or struct member which describes the length of the provided pointer argument. When the length is more complex than a simple argument, i.e. is a function of another parameter, `missing` is returned. In this case, refer to the `.len` field of the argument to get the correct `Expr`.
