```julia
struct Plot <: PGFPlotsX.OptionType
```

これは `pgfplot` コマンドの `\addplot[3][+]` ファミリーに対応しています。

デフォルトのコンストラクタの代わりに、ユーザーコードでは `Plot([options], data, trailing...)` および同様の (`PlotInc`, `Plot3`, `Plot3Inc`) を使用してください。
