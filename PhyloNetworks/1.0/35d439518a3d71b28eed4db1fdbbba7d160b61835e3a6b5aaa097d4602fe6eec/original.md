```
writenewick(net)
writenewick(net, filename)
writenewick(net, IO)
```

Write the parenthetical extended Newick format of a network, as a string, to a file or to an IO buffer / stream. Optional arguments (default values):

  * di (false): write in format for Dendroscope
  * round (false): rounds branch lengths and heritabilities γ
  * digits (3): digits after the decimal place for rounding
  * append (false): if true, appends to the file
  * internallabel (true): if true, writes internal node labels

If the current root placement is not admissible, other placements are tried. The network is updated with this new root placement, if successful.

Uses lower-level function [`writesubtree!`](@ref).
