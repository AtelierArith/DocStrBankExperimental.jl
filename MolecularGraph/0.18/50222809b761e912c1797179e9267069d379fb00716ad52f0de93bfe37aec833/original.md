```
find_queries(mol::MolGraph, query_diagram; subsets=[], filtering=true
    ) -> DictDiGraph, vprops, eprops
```

Find query relationship diagram by the given molecule. The filtered diagram represents query relationship that the molecule have.
