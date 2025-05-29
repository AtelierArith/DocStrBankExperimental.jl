```
Pseudoread(startpos::Integer, endpos::Integer, read::Haplotype)
Pseudoread(query::Union{SAM.Record,BAM.Record}, reference::NucleotideSeq)
```

A stand-in struct for a sequencing read (real or imaginary) represented by its position and differences relative to a reference sequence.
