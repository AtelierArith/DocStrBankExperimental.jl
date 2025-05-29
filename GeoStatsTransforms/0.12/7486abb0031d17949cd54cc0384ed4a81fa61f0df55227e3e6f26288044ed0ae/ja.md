```
Detrend(col₁, col₂, ..., colₙ; degree=1)
Detrend([col₁, col₂, ..., colₙ]; degree=1)
Detrend((col₁, col₂, ..., colₙ); degree=1)
```

与えられた`degree`の多項式で列`col₁`、`col₂`、...、`colₙ`のトレンドを除去する変換。

```
Detrend(regex; degree=1)
```

`regex`に一致する列のトレンドを除去します。

# 例

```julia
Detrend(1, 3, 5)
Detrend([:a, :c, :e])
Detrend(("a", "c", "e"))
Detrend(r"[ace]", degree=2)
Detrend(:)
```

## 参考文献

  * Menafoglio, A., Secchi, P. 2013. [A Universal Kriging predictor for spatially dependent functional data of a Hilbert Space](https://doi.org/10.1214/13-EJS843)
