```
resample(f::Function, x::UVAL_COLLECTION_TYPES, y::UVAL_COLLECTION_TYPES, n::Int, args...; kwargs...)
```

`x`の要素をその不確実な値に従って再サンプリングし、`length(x) = l`の場合は長さ`l`の実現を生成します。次に、`y`についても同様の操作を行います。`x`と`y`の要素は独立して再サンプリングされ、`x`と`y`の要素間に順序依存性はないと仮定します。

次に、長さ`l`のサンプル`x_draw`と`y_draw`に対して`f(x_draw, y_draw, args..., kwargs...)`を呼び出します。このプロセスは`n`回繰り返され、`f`の評価の長さ`n`の分布が得られます。
