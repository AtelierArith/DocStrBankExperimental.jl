```
readmultinewicklevel1(file)
```

Read a text file with a list of trees/networks in extended newick format (one tree per line) and transform them like [`readnewicklevel1`](@ref). Namely, in each tree/network

  * the root is suppressed (becomes of degree 3 if it was of degree 2)
  * any polytomy is resolved arbitrarily
  * any missing branch length is set to 1
  * any branch length above 10 is set to 10 (this assumes branch lengths in coalescent units)
  * any missing γ's are set to (0.1, 0.9)

and more (see [`readnewicklevel1`](@ref)).

See [`PhyloNetworks.readmultinewick`](@extref) to read multiple trees or networks with no modification.

Output: array of HybridNetwork objects.

Each line starting with "(" will be considered as describing one topology. The file can have extra lines that are ignored.
