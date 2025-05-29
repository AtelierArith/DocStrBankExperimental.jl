```
newpedlist,newidtable = set_upg(pedlist, idtable, upgtable)
```

Assigns unknown parent groups (UPG) to unknown parents following the rule in `upgtable` for a pedigree list `pedlist` and the original ID table `idtable` See the following example; 5 UPG and the animals with IDs "A", "B", and "C" are grouped into the 1st UPG and "D" and "E" are grouped into the 2nd UPG.

```
upgtable = Dict("A"=>1, "B"=>1, "C"=>1, "D"=>2, "E"=>2)
```

The "animals" defined as UPG in `upgtable` are eliminated from the pedigree list. If there are parent animals, they are replaced with integer UPG-code larger than the number of real animals. The table `idtable` is also updated accordingly.
