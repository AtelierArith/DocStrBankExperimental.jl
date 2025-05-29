```
transfermatrix(dualpsi,psi,i,j[,transfermat=])
```

Forms the transfer matrix (an MPS `psi` and its dual `dualpsi` contracted along the physical index) between sites `i` and `j` (inclusive). If not specified, the `transfermat` field will initialize to the transfer matrix from the `i-1` site

The form of the transfer matrix must be is as follows (dual wavefunction tensor on top, conjugated)

1 –––––– 3         |         |         |         | 2 –––––– 4

There is no in-place version of this function
