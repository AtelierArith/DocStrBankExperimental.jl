```
compute_saddle(bsn_nfo::BasinInfo, integ; max_iter=10)
```

The algorithm the saddle that lies in  a boundary of the basin of attraction of a dynamical system. When the boundary is fractal, this set is known as the chaotic saddle and is responsible for the transient dynamics of the system. The saddle is computed with the Saddle-Straddle algorithm. It is necessary to define two `generalized basin`, that is we must separate the basin into two sets (see also keyword arguments).

[H. E. Nusse and J. A. Yorke, Dynamics: numerical explorations, Springer, New York, 2012]

## Arguments

  * `bsn_nfo` : structure that holds the information of the basin as well as the map function. This structure is set when the basin is first computed with `basin_stroboscopic_map` or `basin_poincare_map`.
  * `integ` : the matrix containing the information of the basin.
  * `bas_A` : vector with the indices of the attractors that will represent the generalized basin A
  * `bas_B` : vector with the indices of the attractors that will represent the generalized basin B. Notice that `bas_A ∪ bas_B = [1:N]` and `bas_A ∩ bas_B = ∅`

## Keyword arguments

  * `N` : number of points of the saddle to compute
  * `init_tol`: length of the straddle segment

## Example

```
# compute 1000 points between generalized A = [1] and basin B = [2,3]
sa,sb = compute_saddle(bsn, integ_df, [1], [2,3],1000)
# sa is the "left" set and sb the right "set"
```
