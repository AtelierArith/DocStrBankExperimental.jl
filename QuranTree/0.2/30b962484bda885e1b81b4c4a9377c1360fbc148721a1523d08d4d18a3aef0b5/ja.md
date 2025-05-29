```
@desc(expr)
```

`AbstractQuranFeature`の詳細な説明を抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps);
julia> tnzldata = table(tnzl);
julia> feat = parse(Features, select(crpsdata.data, :features)[53])
julia> @desc feat
Stem
────
Negative:
 ├ data: NEG
 ├ desc: Negative particle
 └ ar_label: حرف نفي
Lemma:
 └ data: laA
Special:
 └ data: <in~
```
