```
readfastatodna(filename::String, countPatterns::Bool=false)
```

Read a fasta file to a dataframe containing a column for each site. If `countPatterns` is true, calculate weights and remove identical site patterns to reduce matrix dimension.

Return a tuple containing:

1. data frame of BioSequence DNA sequences, with taxon names in column 1 followed by a column for each site pattern, in columns 2-npatterns;
2. array of weights, one weight for each of the site columns. The length of the weight vector is equal to npatterns.

**Warning**: assumes a *semi-sequential* format, *not interleaved*, where each taxon name appears only once. For this one time, the corresponding sequence may be broken across several lines though.
