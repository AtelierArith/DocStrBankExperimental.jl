```
assign_taxonomy(seq_fasta,ref_fasta; k = 8, n_bootstrap = 100,keep_lp = false,lp=false)
```

Use the [RDP Naive Bayesian Classifier algorithm](https://pubmed.ncbi.nlm.nih.gov/17586664/) to assign taxonomic  classifications based on DNA sequence data. This function takes (the paths to) two fasta files `seq_fasta` and `ref_fasta`, containing target sequences and a reference database respectively. It  returns `Tables.jl` compatible `ClassificationResult`, containing the target sequence IDs,  target sequences, taxonomic classifications and bootstrapped confidence levels.

  * `seq_fasta`: Path to a fasta of sequnces to be classified.
  * `ref_fasta`: Path to a fasta reference database.
  * `k`: Length of kmers to use.
  * `n_bootstrap`: Number of bootstrap iterations to perform.
  * `keep_lp`: Return array of log probabilities alongside classification result if `true`
  * `lp`: Array of log probabilities for the classifier to use.

`ref_fasta` must be a DADA2-formatted reference database.  See [here](https://benjjneb.github.io/dada2/training.html) for examples.
