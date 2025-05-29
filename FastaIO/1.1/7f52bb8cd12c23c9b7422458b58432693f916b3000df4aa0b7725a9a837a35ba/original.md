```
writeentry(fw::FastaWriter, description::AbstractString, sequence)
```

This function writes one entry to the FASTA file, following the specifications detailed in the section titled [The FASTA format](@ref). The `description` is without the initial `'>'` character. The `sequence` can be any iterable object whose elements are convertible to ASCII characters.

Example:

```julia
FastaWriter("somefile.fasta") do fw
    for (desc,seq) in [("GENE1", "GCATT"), ("GENE2", "ATTAGC")]
        writeentry(fw, desc, seq)
    end
end
```
