```
MSA{T}
```

注釈付きの複数配列アライメントのためのストックホルム形式。配列データは `Vector{T}` 型です。

## 例

```julia
using BioStockholm
msa = read(msa_filepath::String, MSA)
msa = parse(MSA, msa_str::String)
msa = parse(MSA{UInt8}, msa_str::String)
write("out.sto", msa)
print(msa)

msa = MSA{Char}(;
    seq = Dict("human"   => "ACACGCGAAA.GCGCAA.CAAACGUGCACGG",
               "chimp"   => "GAAUGUGAAAAACACCA.CUCUUGAGGACCU",
               "bigfoot" => "UUGAG.UUCG..CUCGUUUUCUCGAGUACAC"),
     GC = Dict("SS_cons" => "...<<<.....>>>....<<....>>.....")
)
```

## フィールド

```
seq: seqname => seqdata
GF : per_file_feature => text
GS : seqname => per_seq_feature => text
GC : per_file_feature => seqdata
GR : seqname => per_seq_feature => seqdata
```
