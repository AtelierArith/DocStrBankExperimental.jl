```
@desc(expr)
```

Extract the detailed description of a `AbstractQuranFeature`.

# Examples

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
