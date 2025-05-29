[MASH distances](http://doi.org/10.1186/s13059-016-0997-x), based on MinHash sketches of genome sequences provide rapid genome-scale sequence comparisons when sequence distance (not specific mutations) are all that's required.

A MinHash sketch is made by taking the `s` smallest hash values for kmers of length `k` for a given sequence. The genome distance for two genomes is then essentially the [Jaccard index](https://en.wikipedia.org/wiki/Jaccard_index) of the minhashes, with some additional modification to account for the size of the kmers used.
