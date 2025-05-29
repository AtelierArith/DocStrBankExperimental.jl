```
detect_wada_grid_method(integ, bsn_nfo::BasinInfo; max_iter=10)
```

The algorithm test for Wada basin in a dynamical system. It uses the dynamical system to look if all the atractors are represented in the boundary.

[A. Daza, A. Wagemakers, M. A. F. Sanjuán and J. A. Yorke, Testing for Basins of Wada, Sci. Rep., 5, 16579 (2015)]

## Arguments

  * `integ` : the matrix containing the information of the basin.
  * `bsn_nfo` : structure that holds the information of the basin as well as the map function. This structure is set when the basin is first computed with `basin_stroboscopic_map` or `basin_poincare_map`.

## Keyword arguments

  * `max_iter` : set the maximum depth of subdivisions to look for an atractor. The number of points doubles at each step.
