```
Signal()
```

信号を作成します。 [Vega docs](https://vega.github.io/vega/docs/signals/)

# 例

```julia
# コントロールにリンクされた信号を作成
sig1 = Signal(value=15, bind=(input=:range, min=0, max=50, step=1))

# 式に基づいた信号を作成
sig2 = Signal(update="[0,0.9*bandwidth('$xscale')]")
```
