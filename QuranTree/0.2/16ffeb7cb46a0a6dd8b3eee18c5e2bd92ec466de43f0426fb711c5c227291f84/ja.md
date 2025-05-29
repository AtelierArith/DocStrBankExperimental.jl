```
table(tnzl::TanzilRaw)
```

`TanzilRaw` の読み取り専用配列を `IndexedTable` を使用して表形式の `TanzilData` に変換します。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> tnzldata = table(tnzl);
```
