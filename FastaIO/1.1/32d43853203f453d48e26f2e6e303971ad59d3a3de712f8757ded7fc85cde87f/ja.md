```
readfasta(file::Union{String,IO}, [sequence_type::Type = String])
```

この関数は、FASTAファイル全体を一度に解析し、メモリに格納します。結果は `Vector{Any}` で、その要素は `(description, sequence)` からなるタプルで構成されます。ここで、`description` は `String` であり、`sequence` にはシーケンスデータが含まれ、`sequence_type` オプション引数で定義されたコンテナ型に格納されます（詳細については [The sequence storage type](@ref) セクションを参照してください）。
