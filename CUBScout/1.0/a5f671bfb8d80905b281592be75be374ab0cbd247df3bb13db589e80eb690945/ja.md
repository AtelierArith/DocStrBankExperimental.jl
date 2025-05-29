```
find_seqs(path::AbstractString, match_pattern::Regex)
find_seqs(stream::IO, match_pattern::Regex)
find_seqs(reader::FASTAReader, match_pattern::Regex)
```

`path`（または`reader`またはfastaファイルを指す`IO`）にあるfastaファイルを読み込み、指定されたRegex `match_pattern`に対して*description*フィールドをクエリします。これらの結果は、コドン使用バイアス関数用の参照タプルまたは表現性測定用の参照ベクターのいずれかで提供できます。

# 例

`jldoctest julia> find_seqs(EXAMPLE_DATA_PATH, r"ribosomal")[1:5] 5-element Vector{Bool}:  0  0  0  0  0`
