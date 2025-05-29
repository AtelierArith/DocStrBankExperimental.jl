```
lemma(feat::AbstractQuranFeature)
```

特徴のレマを抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> lemma(parse(QuranFeatures, select(crpsdata[112].data, :features)[1]))
"qaAla"
```
