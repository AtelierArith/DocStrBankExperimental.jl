```
fetchseq(ids::AbstractString::AbstractVector{<:AbstractString}, range::Union{Nothing, AbstractRange} = nothing, revstrand = false; format::SeqFormat = fasta)
```

Fetches sequence data from a database by accession number in either FASTA format or GenBank flatfile format. Nucleotide and protein records may be mixed. Results will be returned in the order provided. Supports NCBI, Ensembl, and UniProt accession numbers.

GenBank format may not work right now.

```julia
fetchseq("AH002844")                # retrive one FASTA NCBI nucleotide record
fetchseq(["CAA41295.1", "NP_000176"]) # retrieve two FASTA NCBI protein records
fetchseq("NC_036893.1", 81_775_230 .+ (1:1_000_000))         # retrive a 1 Mb segment of a FASTA NCBI genomic record
fetchseq("NC_036893.1", 81000000:81999999, true) # retrive a 1 Mb segment of a FASTA NCBI genomic record on the reverse strand
```

`range` and `revstrand` are only valid for nucleotide queries
