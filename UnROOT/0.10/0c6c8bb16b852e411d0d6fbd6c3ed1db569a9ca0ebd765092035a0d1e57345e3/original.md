```
function LazyTree(f::ROOTFile, tree::TTree, treepath, branches; sink = LazyTree)
```

Creates a lazy tree object of the selected branches only. `branches` is vector of `String`, `Regex` or `Pair{Regex, SubstitutionString}`, where the first item is the regex selector and the second item the rename pattern. An alternative  container can be used by providing a sink function. The sink function must take as argument an table with a Tables.jl interface. The table columns are filled with  LazyBranch objects.
