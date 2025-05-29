`matrix2wfst(isym,[osym,] X; W = TropicalWeight{Float32})`

Creates a WFST with weight type `W` and input output tables `isym` and `osym` using the matrix `X`. If `X` is a matrix of dimensions `Ns`x`Nt`, the resulting fst will have `Nt+1` states. Arcs form the `t`-th state of `fst` will go only to the `t+1`-th state and will correspond to the non-zero element of the `t`-th column of `X`.  State `1` and `Nt+1` are initial and final state, respectively.
