```
seq_names(path::AbstractString)
seq_names(reader::FASTAReader)
seq_names(stream::IO)
```

`path`にあるfastaファイルを読み込み、*name*フィールドを返します。これはFASTX関数の上に便利さを追加するだけです。

# 例

```jldoctest
julia> seq_name_vector = seq_names(EXAMPLE_DATA_PATH);

julia> seq_name_vector[1]
"lcl|NC_000964.3_cds_NP_387882.1_1"
```
