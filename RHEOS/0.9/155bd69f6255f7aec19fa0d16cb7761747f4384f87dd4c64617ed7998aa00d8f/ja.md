```
exportcsv(self::Union{RheoTimeData, RheoFreqData}, filedir::String; delimiter=',', colorder=nothing)
```

`RheoTimeData` または `RheoFreqData` タイプを csv 形式にエクスポートします。他のソフトウェアでのプロットや分析に役立つかもしれません。デフォルトでは、完全な時間データが (t, σ, ϵ) の順序でエクスポートされます。部分的な時間データは (t, σ) または (t, ϵ) のいずれかの順序になります。完全な周波数データは (ω, Gp, Gpp) の順序でエクスポートされます。列の順序は、`colorder` 引数に NamedTuple を渡すことでカスタマイズできます。例えば (σ = 1, t = 3, ϵ = 2) は列を (σ, ϵ, t) の順序でエクスポートします。`importcsv` と同様に、区切り文字はキーワード引数で設定できます。
