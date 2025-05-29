Computes a random sample from the determinantal point process defined by the spectral factorization object `L`.

Inputs:

```
`L`: `Eigen` factorization object of an N x N matrix
```

Output:

```
`Y`: A `Vector{Int}` with entries in [1:N].
```

References:

```
Algorithm 18 of \cite{HKPV05}, as described in Algorithm 1 of \cite{KT12}.

@article{HKPV05,
    author = {Hough, J Ben and Krishnapur, Manjunath and Peres, Yuval and Vir'{a}g, B'{a}lint},
    doi = {10.1214/154957806000000078},
    journal = {Probability Surveys},
    pages = {206--229},
    title = {Determinantal Processes and Independence},
    volume = {3},
    year = {2005}
    archivePrefix = {arXiv},
    eprint = {0503110},
}

@article{KT12,
    author = {Kulesza, Alex and Taskar, Ben},
    doi = {10.1561/2200000044},
    journal = {Foundations and Trends in Machine Learning},
    number = {2-3},
    pages = {123--286},
    title = {Determinantal Point Processes for Machine Learning},
    volume = {5},
    year = {2012},
    archivePrefix = {arXiv},
    eprint = {1207.6083},
}

TODO Check loss of orthogonality - a tip from Zelda Mariet
```
