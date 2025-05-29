```
scale!(A::ITensor,x::Number) = rmul!(A,x)
```

Scale the ITensor A by x in-place. May also be written `rmul!`.

```
A .*= x
```
