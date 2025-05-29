```
calc_reality(lgir::LGIrrep, 
             sgops::AbstractVector{SymOperation{D}},
             αβγ::Union{Vector{<:Real},Nothing}=nothing) --> ::(Enum Reality)
```

Compute and return the reality of a `lgir::LGIrrep` using the Herring criterion.

The computed value is one of three integers in ${1,-1,0}$. In practice, this value is returned via a member of the Enum `Reality`, which has instances `REAL = 1`, `PSEUDOREAL = -1`, and `COMPLEX = 0`.

## Optional arguments

As a sanity check, a value of `αβγ` can be provided to check for invariance along a symmetry symmetry line/plane/general point in k-space. The reality must be invariant to this choice.

## Note

The provided space group operations `sgops` **must** be the set reduced by primitive translation vectors; i.e. using `spacegroup(...)` directly is **not** allowable in general (since the irreps we reference only include these "reduced" operations). This reduced set of operations can be obtained e.g. from the Γ point irreps of ISOTROPY's dataset, or alternatively, from `reduce_ops(spacegroup(...), true)`.

## Implementation

The Herring criterion evaluates the following sum

$[∑ χ({β|b}²)]/[g_0/M(k)]$

over symmetry operations ${β|b}$ that take $k → -k$. Here $g_0$ is the order of the point group of the space group and $M(k)$ is the order of star($k$) [both in a primitive basis].

See e.g. Cornwell, p. 150-152 & 187-188 (which we mainly followed), Inui Eq. (13.48),  Dresselhaus, p. 618, or [Herring's original paper](https://doi.org/10.1103/PhysRev.52.361).
