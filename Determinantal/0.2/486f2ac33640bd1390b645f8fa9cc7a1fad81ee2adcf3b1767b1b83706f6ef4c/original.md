```
greedy_subset(L :: AbstractLEnsemble,k)
```

Perform greedy subset selection: find a subset $\mathcal{X}$ of size $k$, such that $\det{L}_{\mathcal{X}}$ is high, by building the set item-by-item and picking at each step the item that maximises the determinant. You can view this as finding an (approximate) mode of the DPP with L-ensemble L.

If $k$ is too large relative to the (numerical) rank of L, the problem is not well-defined as so the algorithm will stop prematurely.

The implementation runs in $\O(nk^2)$ but is not particularly optimised. If the end result looks screwy, it is probably due to numerical instability: try improving the conditioning of $\bL$.

# Example

```@example
x = randn(2,100) #10 points in dim 2
greedy_subset(EllEnsemble(gaussker(x)),12)
#same thing but faster:
greedy_subset(gaussker(x),12)
```
