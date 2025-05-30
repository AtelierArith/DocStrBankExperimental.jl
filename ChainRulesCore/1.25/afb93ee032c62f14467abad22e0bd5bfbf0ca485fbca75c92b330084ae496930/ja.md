```
ignore_derivatives(x)
```

引数の勾配を無視するようにADシステムに指示します。勾配の不必要な計算を避けるために使用できます。

```julia
ignore_derivatives(x) * w
```
