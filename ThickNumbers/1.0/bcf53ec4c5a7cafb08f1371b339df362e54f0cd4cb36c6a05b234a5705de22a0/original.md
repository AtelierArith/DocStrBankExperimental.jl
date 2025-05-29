```
mag(x::ThickNumber)
```

The maximum absolute value of `x`. Required by IEEE Std 1788-2015, Table 9.2.

# Default implementation

The default implementation is

```
mag(x::ThickNumber) = max(abs(loval(x)), abs(hival(x)))
```
