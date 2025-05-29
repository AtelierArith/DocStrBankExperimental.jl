Compute graph layout using stress majorization

Inputs:

```
δ: Matrix of pairwise distances
p: Dimension of embedding (default: 2)
w: Matrix of weights. If not specified, defaults to
       w[i,j] = δ[i,j]^-2 if δ[i,j] is nonzero, or 0 otherwise
X0: Initial guess for the layout. Coordinates are given in rows.
    If not specified, default to random matrix of Gaussians
```

Additional optional keyword arguments control the convergence of the algorithm and the additional output as requested:

```
maxiter:   Maximum number of iterations. Default: 400size(X0, 1)^2
abstols:   Absolute tolerance for convergence of stress.
           The iterations terminate if the difference between two
           successive stresses is less than abstol.
           Default: √(eps(eltype(X0))
reltols:   Relative tolerance for convergence of stress.
           The iterations terminate if the difference between two
           successive stresses relative to the current stress is less than
           reltol. Default: √(eps(eltype(X0))
abstolx:   Absolute tolerance for convergence of layout.
           The iterations terminate if the Frobenius norm of two successive
           layouts is less than abstolx. Default: √(eps(eltype(X0))
verbose:   If true, prints convergence information at each iteration.
           Default: false
returnall: If true, returns all iterates and their associated stresses.
           If false (default), returns the last iterate
```

Output:

```
The final layout X, with coordinates given in rows, unless returnall=true.
```

Reference:

```
The main equation to solve is (8) of:

@incollection{
    author = {Emden R Gansner and Yehuda Koren and Stephen North},
    title = {Graph Drawing by Stress Majorization}
    year={2005},
    isbn={978-3-540-24528-5},
    booktitle={Graph Drawing},
    seriesvolume={3383},
    series={Lecture Notes in Computer Science},
    editor={Pach, J'anos},
    doi={10.1007/978-3-540-31843-9_25},
    publisher={Springer Berlin Heidelberg},
    pages={239--250},
}
```
