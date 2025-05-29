```
readtrees2CF(treefile)
readtrees2CF(vector of trees)
```

Read trees in parenthetical format from a file, or take a vector of trees already read, and calculate the proportion of these trees having a given quartet (concordance factor: CF), for all quartets or for a sample of quartets. Optional arguments include:

  * `quartetfile`: name of text file with list of 4-taxon subsets to be analyzed. If none is specified, the function will list all possible 4-taxon subsets.
  * `whichQ="rand"`: to choose a random sample of 4-taxon subsets
  * `numQ`: size of random sample (ignored if whichQ is not set to "rand")
  * `writeTab=false`: does not write the observedCF to a table (default true)
  * `CFfile`: name of file to save the observedCF (default tableCF.txt)
  * `writeQ=true`: save intermediate files with the list of all 4-taxon subsets and chosen random sample (default false).
  * `writeSummary`: write descriptive stats of input data (default: true)
  * `nexus`: if true, it assumes the gene trees are written in nexus file (default: false)

See also: [`PhyloNetworks.countquartetsintrees`](@extref), which uses a much faster algorithm; [`readtableCF`](@ref) to read a table of quartet CFs directly.
