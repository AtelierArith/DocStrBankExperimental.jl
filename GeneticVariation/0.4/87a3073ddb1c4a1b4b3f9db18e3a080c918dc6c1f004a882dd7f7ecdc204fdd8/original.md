```
NL79(sequences)
```

Compute nucleotide diversity, as described by Nei and Li in 1979.

This measure is defined as the average number of nucleotide differences per site between two DNA sequences in all possible pairs in the sample population, and is often denoted by the greek letter pi.

`Sequences` should be any iterable that yields biosequence types.

# Examples

```jldoctest
julia> testSeqs = [dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAACTTTTACCCCCGGGGG",
                   dna"AAAAATTTTACCCCCGTGGG",
                   dna"AAAAATTTTACCCCCGTGGG",
                   dna"AAAACTTTTTCCCCCGTAGG",
                   dna"AAAACTTTTTCCCCCGTAGG",
                   dna"AAAAATTTTTCCCCCGGAGG",
                   dna"AAAAATTTTTCCCCCGGAGG"]
10-element Array{BioSequences.BioSequence{BioSequences.DNAAlphabet{4}},1}:
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAACTTTTACCCCCGGGGG
 AAAAATTTTACCCCCGTGGG
 AAAAATTTTACCCCCGTGGG
 AAAACTTTTTCCCCCGTAGG
 AAAACTTTTTCCCCCGTAGG
 AAAAATTTTTCCCCCGGAGG
 AAAAATTTTTCCCCCGGAGG

 julia> NL79(testSeqs)
 0.096

```
