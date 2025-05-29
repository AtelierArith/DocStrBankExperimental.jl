```
pointwisemult!(w::CeedVector, x::CeedVector, y::CeedVector)
```

`w`を`x .* y`で上書きします。`x`、`y`、および`w`の任意の部分集合が同じベクトルである可能性があります。`w`を返します。
