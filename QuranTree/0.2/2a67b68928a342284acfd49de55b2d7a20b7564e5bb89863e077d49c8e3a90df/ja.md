```
table(crps::CorpusRaw)
```

`CorpusRaw` の読み取り専用配列を `IndexedTable` を使用して表形式の `CorpusData` に変換します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps);
```
