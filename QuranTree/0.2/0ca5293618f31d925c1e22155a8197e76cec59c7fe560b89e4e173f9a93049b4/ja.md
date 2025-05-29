```
load(data::QuranData)
```

生の `QuranData` を `ReadOnlyArray` として、コーランコーパスとタンジルデータの両方にロードします。

# 例

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data);
```
