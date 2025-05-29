## `spectral_cut`

`spectral_cut` will produce a spectral cut partition of the graph into two pieces.

Special cases

  * if your graph is disconnected, then we will partition it into the

largest connected component (chosen arbitrary if there are multiple) and produce a cut of just the largest connected component.

  * if your graph is a single node, we will partition it into the empty

cut.

## Output

The output has type SpectralCut We always return the smaller side of the cut in terms of total volume.

## Inputs

  * `A`: The sparse matrix or martrix network that you want to find the spectral cut for.
  * `checksym`: Should we check symmetry? Don't set this to false unless you have checked symmetry in another call. *This may go away in future interfaces*
  * `ccwarn`: Turn off the warning for disconnected graphs. This useful in larger subroutines where this is handled through another mechanism.
