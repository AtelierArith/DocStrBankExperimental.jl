```
CodonDict
```

The `CodonDict` type defines how codons are translated, and is essential for calculating codon usage bias as it identifies stop codons and each amino acid's degeneracy. A default codon dictionary is provided (`default_codon_dict`), or a user can make their own using the `make_codon_dict` function.

### Fields

  * `codons`: the 64 codons, in alphabetical order
  * `AA`: corresponding amino acid for each codon (64 entries long)
  * `AA_nostops`: same as AA, but with stop codons removed
  * `uniqueAA`: unique amino acid names including stop codons. Under a standard translation table, this is 21 amino acids long
  * `uniqueAA`: same as uniqueAA, but with stop codons removed
  * `uniqueI`: a vector of the same length as uniqueAA, containing vectors of the indices of each codon for that amino acid. For instance, the first entry corresponds to Lysine, and contains the vector `[1, 3]`, corresponding to the positions of codons AAA and AAG in the codons field
  * `uniqueI_nostops`: same as uniqueI, but with stop codons removed
  * `deg`: a vector of the same length as uniqueAA, containing the degeneracy for each amino acid.
  * `deg_nostops`: same as deg, but with stop codons removed
  * `stop_mask`: a Boolean vector of length 64 which is false for stop codons. This is used to remove stop codons when calculating codon usage bias.

### Notes

Generally, CUBScout users shouldn't need to interact with the `CodonDict` type, as the standard genetic code is applied by default. Details for constructing a custom `CodonDict` are documented under the `make_CodonDict` function.
