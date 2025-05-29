```
special(feat::AbstractQuranFeature)
```

トークンの特別な特徴を抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> special(parse(QuranFeatures, select(crpsdata.data, :features)[53]))
"<in~"
```
