```
XPRS_MPSOBJNAME
```

When reading an MPS file, this control determines which neutral row will be read as the objective function. (string)

If this control is set when reading a multi-objective MPS file, only the named objective will be read; all other objectives will be ignored. As with all string controls, this is of length 64 characters plus a null terminator, `0`.

Default value: 64 blanks

Domain: ?
