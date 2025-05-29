```
chapter_name(quran::AbstractQuran, transliterate::Bool=false; lang::Symbol=:arabic)
```

入力されたクルアーンの章名を、`:arabic`（デフォルト）または`:english`のいずれかで抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> chapter_name(crpsdata[13][2][1])
"ٱلرَّعْد"
```
