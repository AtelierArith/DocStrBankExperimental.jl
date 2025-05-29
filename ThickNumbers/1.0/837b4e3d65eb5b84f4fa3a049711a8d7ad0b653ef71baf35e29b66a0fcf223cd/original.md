```
mid(x::ThickNumber)
```

The midpoint of the span of `x`. Required by IEEE Std 1788-2015, Table 9.2.

# Default implementation

The default implementation is

```
mid(x::ThickNumber) = (loval(x) + hival(x))/2
```
