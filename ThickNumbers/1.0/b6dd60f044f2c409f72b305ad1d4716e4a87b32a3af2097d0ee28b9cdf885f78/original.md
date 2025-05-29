```
mig(x::ThickNumber)
```

The minimum absolute value of `x`. Required by IEEE Std 1788-2015, Table 9.2.

# Default implementation

The default implementation checks to see if the set contains zero, and if so returns zero. Otherwise, it returns the minimum absolute value of the endpoints:

```
mig(x::ThickNumber) = zero(T) ∈ x ? zero(T) : min(abs(loval(x)), abs(hival(x)))
```
