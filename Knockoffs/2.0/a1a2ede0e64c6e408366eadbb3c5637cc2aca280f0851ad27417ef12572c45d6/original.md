```
solve_MVR(Σ::AbstractMatrix)
```

Solves the minimum variance-based reconstructability problem for fixed-X and model-X knockoffs given correlation matrix Σ. Users should call `solve_s`  instead of this function. 

See algorithm 1 of "Powerful knockoffs via minimizing  reconstructability" by Spector, Asher, and Lucas Janson (2020) https://arxiv.org/pdf/2011.14625.pdf
