```
words(quran::AbstractQuran)
```

Extract words of the input quran.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> words(tnzldata[1][7])[1]
"صِرَٰطَ"
```
