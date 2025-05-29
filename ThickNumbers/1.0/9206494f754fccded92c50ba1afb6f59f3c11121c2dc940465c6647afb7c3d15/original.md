```
wid(x::ThickNumber)
```

The width of the span of `x`. Required by IEEE Std 1788-2015, Table 9.2.

# Default implementation

The default implementation is

```
wid(x::ThickNumber) = hival(x) - loval(x)
```
