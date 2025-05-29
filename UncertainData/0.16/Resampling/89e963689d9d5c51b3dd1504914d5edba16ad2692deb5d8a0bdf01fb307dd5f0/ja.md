```
resample(f::Function, x::UVAL_COLLECTION_TYPES, n::Int, args...; kwargs...)
```

`x`の要素をその不確実な値に従って再サンプリングし、`length(x) = l` の場合は長さ`l`の実現を生成します。`x`の要素は独立して再サンプリングされ、要素間に順序依存性はないと仮定します。その後、与えられた`args`と`kwargs`を使って長さ`l`のサンプルに対して`f(x, args...; kwargs...)`を呼び出します。このプロセスは`n`回繰り返され、`f`の評価の長さ`n`の分布が得られます。
