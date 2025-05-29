```
scale!(A::ITensor,x::Number) = rmul!(A,x)
```

ITensor Aをxでインプレースでスケーリングします。`rmul!`とも書けます。

```
A .*= x
```
