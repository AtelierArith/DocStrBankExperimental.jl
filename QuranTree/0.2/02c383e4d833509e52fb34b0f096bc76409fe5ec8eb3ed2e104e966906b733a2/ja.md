```
root(feat::AbstractQuranFeature)
```

特徴のルートを抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> root(parse(QuranFeatures, select(crpsdata[112].data, :features)[1]))
"qwl"
```
