```julia
Plot(x, y; ...)
Plot(x, y, l; kind, config, kwargs...)

```

`kind`のタイプの1つのトレースを持つプロットを構築し、`x`をxに、`y`をyに設定します。すべてのキーワード引数は、構築されたトレースに直接キーワード引数として渡されます。

**注意**: `y`が行列の場合、`y`の各列に対して1つのトレースが構築されます。

**注意**: `x`と`y`の両方が行列である場合、同じ数の列（例えば`N`）を持っている必要があります。次に、`N`個のトレースが構築され、`x`の`i`番目の列が`y`の`i`番目の列とペアになります。 ```
