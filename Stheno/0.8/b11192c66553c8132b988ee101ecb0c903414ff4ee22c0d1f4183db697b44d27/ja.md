```
additive_gp(fs)
```

は次のGPを生成します。

```julia
sum(fs[1](x[1]) + fs[2](x[2]) + ... + fs[D](x[D]))
```

`length(fs)`が使用する入力の次元と同じである必要があります。
