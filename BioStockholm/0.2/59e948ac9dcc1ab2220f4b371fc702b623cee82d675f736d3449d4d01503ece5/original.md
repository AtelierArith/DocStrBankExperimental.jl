```
MSA{T}
```

Stockholm format for multiple sequence alignment with annotations. Sequence data is of type `Vector{T}`.

## Examples

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

## Fields

```
seq: seqname => seqdata
GF : per_file_feature => text
GS : seqname => per_seq_feature => text
GC : per_file_feature => seqdata
GR : seqname => per_seq_feature => seqdata
```
