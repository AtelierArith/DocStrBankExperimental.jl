```
isisomorph(tree1::CladoTree, tree2::CladoTree) :: Bool
isisomorph(tree1::ChronoTree, tree2::ChronoTree) :: Bool
```

Test if two trees are isomorphic. 

When both phylogenetic tree are dated, the isomorphism implies that branch  lengths are correspondingly equal; otherwise, only the tree topology are  compared.
