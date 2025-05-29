```
@data(expr)
```

データプロパティオブジェクトを抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps);
julia> tnzldata = table(tnzl);
julia> feat = parse(Features, select(crpsdata.data, :features)[53])
julia> @data feat
:NEG
```
