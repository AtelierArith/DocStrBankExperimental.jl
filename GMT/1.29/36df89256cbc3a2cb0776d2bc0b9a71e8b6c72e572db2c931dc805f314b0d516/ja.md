```
stairs(cmd0::String="", arg1=nothing; step=:post, kwargs...)
```

階段関数をプロットします。`step` パラメータは以下の値を取ることができます：

`:post` - デフォルト。線はまず x に沿って移動し、次に y に沿って移動します。`:pre` - 線はまず y に沿って移動し、次に x に沿って移動します。

例：

```
x = linspace(0, 4*pi, 50);
stairs(x, sin.(x), show=true)
```
