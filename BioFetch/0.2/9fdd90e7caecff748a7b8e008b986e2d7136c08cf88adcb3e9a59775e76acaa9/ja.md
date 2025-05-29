```
fetchseq(ids::AbstractString::AbstractVector{<:AbstractString}, range::Union{Nothing, AbstractRange} = nothing, revstrand = false; format::SeqFormat = fasta)
```

アクセッション番号によってデータベースから配列データを取得します。出力形式はFASTA形式またはGenBankフラットファイル形式のいずれかです。ヌクレオチドおよびタンパク質のレコードを混在させることができます。結果は提供された順序で返されます。NCBI、Ensembl、およびUniProtのアクセッション番号をサポートしています。

現在、GenBank形式は正しく動作しない可能性があります。

```julia
fetchseq("AH002844")                # 1つのFASTA NCBIヌクレオチドレコードを取得
fetchseq(["CAA41295.1", "NP_000176"]) # 2つのFASTA NCBIタンパク質レコードを取得
fetchseq("NC_036893.1", 81_775_230 .+ (1:1_000_000))         # 1 MbのFASTA NCBIゲノムレコードのセグメントを取得
fetchseq("NC_036893.1", 81000000:81999999, true) # 逆鎖上のFASTA NCBIゲノムレコードの1 Mbセグメントを取得
```

`range`と`revstrand`はヌクレオチドクエリにのみ有効です。
