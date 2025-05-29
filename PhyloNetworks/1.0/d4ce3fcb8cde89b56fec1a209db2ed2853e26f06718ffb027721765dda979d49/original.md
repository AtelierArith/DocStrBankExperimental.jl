```
readmultinewick_files(listfile; relative2listfile=true)
```

Read the list of file names in `listfile`, then read all the trees in each of these files. Output: vector of vectors of trees (networks with h>0 allowed).

`listfile` should be the name of a file containing the path/name to multiple bootstrap files, one on each line (no header). Each named bootstrap file should contain multiple trees, one per line (such as bootstrap trees from a single gene).

The path/name to each bootstrap file should be relative to `listfile`. Otherwise, use option `relative2listfile=false`, in which case the file names are interpreted as usual: relative to the user's current directory if not given as absolute paths.
