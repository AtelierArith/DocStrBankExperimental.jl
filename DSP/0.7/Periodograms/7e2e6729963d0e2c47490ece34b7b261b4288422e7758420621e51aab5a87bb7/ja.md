```
mt_pgram(s; onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, nw=4, ntapers=iceil(2nw)-1, window=dpss(length(s), nw, ntapers))
mt_pgram(signal::AbstractVector, config::MTConfig)
```

信号 `s` のマルチテーパー周期ogramを計算します。

`window` が指定されていない場合、信号は `ntapers` 個の離散的プロレート球面系列でテーパーされ、時間-帯域幅積は `nw` です。各系列は同じ重みが付けられます。適応型マルチテーパーは（まだ）サポートされていません。

`window` が指定されている場合、各列がテーパーとして適用されます。周期ogramの合計は `window` の総平方和で正規化されます。

`Periodogram` を返します。

[`mt_pgram!`](@ref) および [`MTConfig`](@ref) も参照してください。
