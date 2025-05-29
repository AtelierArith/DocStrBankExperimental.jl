```
readnexus_treeblock(filename, treereader=readnewick, args...;
                    reticulate=true, stringmodifier=[r"#(\d+)" => s"#H\1"])
```

Read the *first* "trees" block of a nexus-formatted file, using the translate table if present, and return a vector of `HybridNetwork`s. Information inside `[&...]` are interpreted as comments and are discarded by the default tree reader. Optional arguments `args` are passed to the tree reader.

For the nexus format, see [Maddison, Swofford & Maddison (1997)](https://doi.org/10.1093/sysbio/46.4.590).

Unless `reticulate` is false, the following is done to read networks with reticulations.

Prior to reading each phylogeny, each instance of `#number` is replaced by `#Hnumber` to fit the standard extended Newick format at hybrid nodes. This behavior can be changed with option `stringmodifier`, which should be a vector of pairs accepted by `replace`.

Inheritance γ values are assumed to be given within "comment" blocks at *minor* hybrid edges (cut as tips to form the extended Newick) like this for example, as output by bacter ([Vaughan et al. 2017](http://dx.doi.org/10.1534/genetics.116.193425)):

```
#11[&conv=0, relSize=0.08, ...
```

or like this, as output by SpeciesNetwork ([Zhang et al. 2018](https://doi.org/10.1093/molbev/msx307)):

```
#H11[&gamma=0.08]
```

In this example, the corresponding edge to hybrid H11 has γ=0.08.
