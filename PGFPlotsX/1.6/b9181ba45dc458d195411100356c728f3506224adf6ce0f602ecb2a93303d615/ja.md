```
Plot([options::Options], data, trailing...)
```

与えられた `data`（例 [`Coordinates`](@ref), [`Table`](@ref), [`Expression`](@ref), …）と `options` を使用してプロットを作成します。デフォルトでは `options` は空です。

PGFPlots の `\addplot` に対応します。

`trailing` は、終了 `;` の前に `print_tex` を使用して出力される *トレーリングパスコマンド*（例 `\closedcycle`、PGFPlots マニュアルを参照）を提供するために使用できます。
