```
chapter_name(quran::AbstractQuran, transliterate::Bool=false; lang::Symbol=:arabic)
```

Extract the chapter name of the input quran, in either `:arabic` (default) or `:english`

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> chapter_name(crpsdata[13][2][1])
"ٱلرَّعْد"
```
