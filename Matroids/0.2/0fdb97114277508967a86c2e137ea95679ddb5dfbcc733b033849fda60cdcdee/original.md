```
incidence_matrix(g::EasyMultiGraph)
```

Create a signed incidence matrix for `g`. Multiple edges become repeated columns. Loops become all-zero columns. The order of the columns exactly matches the output of `edges(g)`.
