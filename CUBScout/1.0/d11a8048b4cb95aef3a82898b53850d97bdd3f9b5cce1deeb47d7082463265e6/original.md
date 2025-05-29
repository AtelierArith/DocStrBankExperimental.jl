```
make_CodonDict(filepath::AbstractString, delimiter::AbstractChar = '	')
```

Make a custom codon dictionary for organisms with non-standard genetic code. `filepath` points to a delimited file with two columns and no header. The first column should be codons, and the second column their corresponding amino acid. Avoid spaces and special characters (e.g., write GlutamicAcid instead of Glutamic Acid). Stop codons can be coded as Stop, stop, STOP, or *. If delimited using any character outside of tab, supply the delimiter as the second argument as Char, not a string (e.g. `','` not `","`). `make_CodonDict` uses `readdlm` from `DelimitedFiles`; it's a good idea to check whether `readdlm` parses your file correctly before passing to `make_CodonDict`

# Examples

```jldoctest
julia> my_CodonDict = make_CodonDict(CUBScout.CodonDict_PATH)
CodonDict(BioSequences.LongSequence{BioSequences.DNAAlphabet{2}}[AAA, AAC, AAG, AAT, ACA, ACC, ACG, ACT, AGA, AGC  …  TCG, TCT, TGA, TGC, TGG, TGT, TTA, TTC, TTG, TTT], ["Lysine", "Asparagine", "Lysine", "Asparagine", "Threonine", "Threonine", "Threonine", "Threonine", "Arginine", "Serine"  …  "Serine", "Serine", "Stop", "Cysteine", "Tryptophan", "Cysteine", "Leucine", "Phenylalanine", "Leucine", "Phenylalanine"], ["Lysine", "Asparagine", "Lysine", "Asparagine", "Threonine", "Threonine", "Threonine", "Threonine", "Arginine", "Serine"  …  "Serine", "Serine", "Serine", "Cysteine", "Tryptophan", "Cysteine", "Leucine", "Phenylalanine", "Leucine", "Phenylalanine"], ["Lysine", "Asparagine", "Threonine", "Arginine", "Serine", "Isoleucine", "Methionine", "Glutamine", "Histidine", "Proline"  …  "Glutamicacid", "Asparticacid", "Alanine", "Glycine", "Valine", "Stop", "Tyrosine", "Cysteine", "Tryptophan", "Phenylalanine"], ["Lysine", "Asparagine", "Threonine", "Arginine", "Serine", "Isoleucine", "Methionine", "Glutamine", "Histidine", "Proline", "Leucine", "Glutamicacid", "Asparticacid", "Alanine", "Glycine", "Valine", "Tyrosine", "Cysteine", "Tryptophan", "Phenylalanine"], Vector{Int32}[[1, 3], [2, 4], [5, 6, 7, 8], [9, 11, 25, 26, 27, 28], [10, 12, 53, 54, 55, 56], [13, 14, 16], [15], [17, 19], [18, 20], [21, 22, 23, 24]  …  [33, 35], [34, 36], [37, 38, 39, 40], [41, 42, 43, 44], [45, 46, 47, 48], [49, 51, 57], [50, 52], [58, 60], [59], [62, 64]], Vector{Int32}[[1, 3], [2, 4], [5, 6, 7, 8], [9, 11, 25, 26, 27, 28], [10, 12, 51, 52, 53, 54], [13, 14, 16], [15], [17, 19], [18, 20], [21, 22, 23, 24], [29, 30, 31, 32, 58, 60], [33, 35], [34, 36], [37, 38, 39, 40], [41, 42, 43, 44], [45, 46, 47, 48], [49, 50], [55, 57], [56], [59, 61]], Int32[2, 2, 4, 6, 6, 3, 1, 2, 2, 4  …  2, 2, 4, 4, 4, 3, 2, 2, 1, 2], Int32[2, 2, 4, 6, 6, 3, 1, 2, 2, 4, 6, 2, 2, 4, 4, 4, 2, 2, 1, 2], Bool[1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  1, 1, 0, 1, 1, 1, 1, 1, 1, 1])

julia> typeof(my_CodonDict)
CodonDict

julia> fieldnames(CodonDict)
(:codons, :AA, :AA_nostops, :uniqueAA, :uniqueAA_nostops, :uniqueI, :uniqueI_nostops, :deg, :deg_nostops, :stop_mask)
```
