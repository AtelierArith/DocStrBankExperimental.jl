```
verses(quran::AbstractQuran; number=false, start_end=true)
```

`AbstractQuran`オブジェクトの節を抽出します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps)
julia> tnzldata = table(tnzl)
julia> verses(crpsdata[1])[7]
"Sira`Ta {l~a*iyna >anoEamota Ealayohimo gayori {lomagoDuwbi Ealayohimo walaA {lD~aA^l~iyna"
julia> verses(crpsdata[113:114], number=true)[1]
"113:(1,5)"
julia> verses(crpsdata[113:114], number=true, start_end=false)[1]
([113], [1, 2, 3, 4, 5])
```
