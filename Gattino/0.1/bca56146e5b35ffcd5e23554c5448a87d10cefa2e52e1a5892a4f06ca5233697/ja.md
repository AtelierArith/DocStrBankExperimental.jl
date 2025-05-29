```julia
hist -> ::AbstractContext
```

`hist_plot!`の非変異バージョン – `Context`を作成し、その後`hist_plot!`を使用してヒストグラム/棒グラフを描画します（引数に応じて）。`scatter`や`line`と同様に、引数はプロット関数に渡され、これらの関数から使用される可能性があります。`width`と`height`も提供できます。このタイプのプロットでは、`x`のみが非数値であることができます。

この関数に関連して、`context_plotting`の`vbars!`についても言及する必要があります。
