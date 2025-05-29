```
words(quran::AbstractQuran)
```

入力されたコーランの単語を抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> words(tnzldata[1][7])[1]
"صِرَٰطَ"
```
