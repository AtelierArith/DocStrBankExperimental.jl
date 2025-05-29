```
mix = mixture(signals, amps, [delays::Vector{Int}])
mixes = mixture(signals, amps::Vector{Vector}, [delays::Vector{Vector{Int}}])
```

振幅 `amps` と `delays` を使用して信号を混合します（`delays` はサンプルで指定されます）。`amps` とオプションの `delays` がベクトルのベクトルである場合、混合のベクトルが返されます。ベクトルのベクトルは `M = reduce(hcat, mixes)` を使用して行列に変換されます。

返される信号は、遅延の最大差に対応する入力信号よりも短くなります。例えば、`delays = [-2,0,5]` の場合、返される混合は7サンプル短くなります。
