```
joindbms(dbms)
joindbms(dbms, visibleindexes)
```

Joins the DBMs given by the vector `dbms` by joining each layer of RBMs. The weights cross-linking the models are initialized with zeros.

If the vector `visibleindexes` is specified, it is supposed to contain in the i'th entry an indexing vector that determines the positions in the combined DBM for the visible nodes of the i'th of the `dbms`. By default the indexes of the visible nodes are assumed to be consecutive.
